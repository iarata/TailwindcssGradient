# TailwindcssTextGradient
A trick for making a moving gradient as the text color.

## I. Gradient for Text Color
First we have to set the gradient in way to be used with text

Add the following code src/styles.css:

```
  ...
  @tailwind utilities

  @layer utilities {
    .text-gradient {
      background-clip: text;
      -webkit-text-fill-color: transparent;
    }
  }
```

### Usage
You can use this code like this:
```
  <div class="text-gradient bg-gradient-to-r from-pink-500 to-yellow-500">
    Moving Gradient Text
  </div>
```

## II. Animation
For making the gradient to animate add the following code to your tailwind config.js file:
```
  theme: {
      extend: {
        animation: {
          'gradient-x': 'gradient-x 10s ease infinite',
          'gradient-y': 'gradient-y 10s ease infinite',
          'gradient-xy': 'gradient-xy 10s ease infinite',
        },
        keyframes: {
          'gradient-y': {
            '0%, 100%': {
              'background-size': '400% 400%',
              'background-position': 'center top'
            },
            '50%': {
              'background-size': '200% 200%',
              'background-position': 'center center'
            }
          },
          'gradient-x': {
            '0%, 100%': {
              'background-size': '200% 200%',
              'background-position': 'left center'
            },
            '50%': {
              'background-size': '200% 200%',
              'background-position': 'right center'
            }
          },
          'gradient-xy': {
            '0%, 100%': {
              'background-size': '400% 400%',
              'background-position': 'left center'
            },
            '50%': {
              'background-size': '200% 200%',
              'background-position': 'right center'
            }
          }
        },
      },
    }
```
### Usage
You can use the animations like this:
```
  <div class="text-gradient bg-gradient-to-r from-pink-500 to-yellow-500 animate-gradient-x">
    Moving Gradient Text (X-Axis)
  </div>

  <div class="text-gradient bg-gradient-to-r from-pink-500 to-yellow-500 animate-gradient-y">
    Moving Gradient Text (Y-Axis)
  </div>

  <div class="text-gradient bg-gradient-to-r from-pink-500 to-yellow-500 animate-gradient-xy">
    Moving Gradient Text (XY-Axis)
  </div>
```
