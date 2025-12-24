# Scripting

## How it works

As said before, this is not an animation program like others. _KODX Animation_ is a generator. To create animations from your scripts, you must provide instructions on how the text, sounds, terminal and other elements will behave.

## Workflow

It is **highly** recommended to write the code in a real editor (VSC, Notepad++, Cursor...), and then copy/paste it into the textarea in the animator. That way, you will be able to make the most of the autocomplete function and visual style you're already used to. Nevertheless, no worries, you will still be able to edit the code in the program.

## Instructions

Instructions are double-hashed (`##`) comments at the end of each line of your code. Generally, you will provide instructions indicating a `property` followed by a `value`, and separated with a space, although there are exceptions for this.

The best way to illustrate the concept of instructions is with a quick example:

```python
# Type your code here! ## wait 5 for 25 wait 10
print('This is a test') ## wait 5 for voice wait 10
```

Don't worry about the instructions themselves yet. Instead, note how **every line** has an instructions indication.

This is crucial. **Every line in your code must have at least one instruction. Otherwise, the animation will not export.**

You can add a space between the last character of your code and the `##`:

```python
print('Hello world') ## for 15
```

Or you can keep them together:

```python
print('Hello world')## for 15
```

If you ever need to add visible spaces after your line, just add one more:

```python
print('Hello world')   ## for 15
```

_(I wanted 2 spaces, so I typed 3)_

## Code instructions

There's two instructions you will use to indicate how you want your main code to be animated.

### Instruction `for x`

_(being `x` the number of frames you want the animation to last)_

Your code will be "typed" for `x` amount of frames. Keyboard sounds will adapt to the speed automatically. Zero is **not** a valid amount and will throw an error.

Optionally, you can set the line to be narrated using `for voice`. The animation will be as long as the generated audio.

An optional setting you can apply to `for voice` is `speed`.

```python
# Valid code ## for voice
# Valid code ## for voice +35%
# Valid code ## for voice -15%
# Invalid code ## for voice 35%
```

The default value of speed is 20%, which is a natural talking pace.

### Instruction `wait x`

_(being `x` the number of frames you want the code to wait for)_

Nothing will happen for `x` frames. Use it to leave some air between lines and let the viewer process. Zero is **not** a valid amount and will throw an error.

It is usually used both **before** and **after** a `for` animation, but you can partially or completely skip it to create different styles and paces.

```python
def my_func(): ## wait 5 for voice wait 6
    print("Hello World") ## wait 3 for voice +35%
    # This will print a line ## for 20
    return 0 ## for voice wait 15
```

### Line break

You can use the `wait` instruction to create line breaks. Make sure never to leave a blank line without at least a `wait` instruction!

```python
print("First line") ## for 18 wait 4
## wait 5
print("Third line") ## wait 5 for 18 wait 10
```

## Terminal instructions

All terminal instructions begin with the keyword `terminal`. Terminal instructions are all written in one line. If this feels unconfortable for you (it will, when you're dealing with long commands), you can look up how you can enable word wrap in your preferred code editor (_in VSC, you can do it by pressing `Alt`+`Z`_)

When you're using the terminal in your animation, **never begin a line with a terminal instruction. It will throw an error.** [Here is](#terminal-usage) what you can do instead.

Here below you can see how the different terminal instructions work. Note that `x` represents the number of frames you want the animation to be, and parameters between curly brackets (`{example}`) are optional: you can add them or not, it will work both ways.

### `terminal open x {sound}` and `terminal close x {sound}`

These are two of the three **only** async instructions in _KODX Animation_, which means that other instructions can start or keep running while these are.

However, you won't normally want other things happening while the terminal is opening or closing. To prevent the default async behaviour, add a `wait x` instruction immediately after these instructions (set the x to be the same as the one in the open/close instruction)

A normal amount of frames for this animation would be `15`. Tweak this value to open/close the terminal faster/slower.

You can optionally modify the `sound` that the terminal will make while opening/closing. The default sound for this animation is `whoosh` (see all available sounds [here](#available-sounds)). If you don't specify a sound for this instruction, the default will be played. You can also set the sound to `none`, and no sound will be played.

Here are a couple of examples of the usage of `terminal open x` and `terminal close x`:

```python
## terminal open 15 wait 15
## terminal close 15 none wait 15
## terminal open 20 error3 wait 20
```

### `terminal write |text| x color {sound}`

With this instruction, you will be able to type text on the terminal just like you did with the code.

First, specify the text you want to be **added** between two pipes (`|`). This text will be inserted right after what is already written (for line breaks, see [`terminal n`](#terminal-n-sound))

> To replicate the style of a real terminal, you can add a _greater than_ symbol (`>`) before each terminal line

After writing your text, indicate the amount of frames you want your animation to last. Zero is **not** a valid amount.

Immediately after, indicate the color you want your text to be. Available colors are `white`, `grey`, `red`, `green`, `blue`, and `yellow`. 

> Parameter `color` is commonly forgotten when coding. Make sure to include it to prevent errors!

Finally, you can decide to specify the sound that typing will make. This is an optional parameter. Default value is `beep`, and you can change it to `key` to use mechanical keyboard sounds; or to `none` to play no sound.

An example of usage can be found in the next section.

### `terminal n {sound}`

This instruction will do a line break in the terminal. If you don't use it, texts from the different `write` instructions will all be inserted in the same line.

Regarding the sound, this is, again, an optional parameter. The default value is `beep-intro`. You can use `key-intro` for a mechanical keyboard enter key sound. You can also set it to `none` for no sound at all. Finally, you can also use any of the sounds in the [sound list](#available-sounds).

Here is a practical example using different styles and sounds, and making use of the `terminal write` and `terminal n` instructions:

```python
## wait 5 terminal open 15 wait 15 terminal write |> Insert your name| 20 yellow wait 4 terminal n terminal write |> | 1 grey wait 9 terminal write |Bob| 6 white key wait 7 terminal n key-intro wait 10
```

### `terminal cls`

This instruction will clear the terminal.

**Closing the terminal does not clear it**. The text in the terminal will be stored even if you close and reopen the terminal. In order to clear the terminal after closing it, just execute both instructions in the correct order:

```python
## terminal close 15 wait 15 terminal cls
```

You can also not clear the terminal after closing it to continue adding lines later, which is a common practise as well.

### Terminal usage

**Never begin a line with a terminal instruction. It will throw an error and your animation will not export properly.** Instead, use the terminal instructions in a line after other non-terminal instructions:

```python
print("Hello World!") ## for 20 terminal open 15 wait 15 ...
```

Or even better, start a line with a `wait` instruction:

```python
## wait 5 terminal open 15 wait 15 ...
```

## Additional instructions

### `sound x`

This is the third and last async instruction in this program (see [terminal open/close](#terminal-open-x-sound-and-terminal-close-x-sound) for more info about async instructions)

Adding a sound won't freeze the program; you will still be able to run other instructions.

[Here are](#available-sounds) all the available sounds.

## Available sounds

- `notification`
- `get_out`
- `error-windows`
- `error1`
- `error3`
- `whoosh`
- `whoosh-long`
- `whoosh-short`

## Code Example #1

In this example, you'll see an advanced, real use of the instructions that apply mainly on code. [Click here](https://www.instagram.com/reel/DPnw_VOkw-G/) to see the animation result. You will get used to 'guessing' the amount of frames you want a certain animation to last. Anyways, there's always an amount of trial an error.

```python
# Please help me ## for voice
# find the mistake ## for voice
# in this code! ## for voice wait 14
## wait 5
x = 0.1 + 0.2 ## wait 6 for 10 wait 15
if x == 0.3: ## wait 5 for 15 wait 20
    print("yes") ## wait 4 for 15 wait 12
else: ## wait 4 for 10 wait 10
    print("no") ## wait 5 for 13 wait 15
## wait 5 terminal open 15 wait 15 terminal write |> no| 5 yellow wait 18
```

## Code Example #2

Here, you'll see an example with a more advanced usage of the terminal. You can watch the animation result [here](https://www.instagram.com/reel/DQOAhylEY_k/).

```python
# I coded Reddit ## for voice wait 13
# Look: ## wait 4 for voice wait 10
## wait 5
post("I like dogs") ## wait 5 for 15 wait 15
## wait 5 terminal open 15 notification wait 10 terminal write |> meowLvr73| 15 blue none wait 14 terminal n none terminal write |  Actually...| 10 yellow wait 13 terminal n terminal write |  Cats are superior.| 18 yellow wait 15 terminal n none terminal n notification terminal write |> petExpert08| 15 blue none wait 16 terminal n none terminal write |  You’re both wrong.| 20 yellow wait 14 terminal n none terminal write |  Goldfish are the best| 23 yellow wait 15 terminal n error3 terminal cls wait 4 terminal write |> Thread deleted by mods.| 25 red wait 15
# Easy! ## wait 3 for voice wait 15
```