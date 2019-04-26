# Core Grid

> A CSS grid that streamlines layout development

Core Grid is a modern flexbox grid system that aims to solve several issues with the standard 12-column model. To improve the developer experience, the class naming system has been streamlined so that class lists can be consise, yet expressive. For greater control over the layout across devices, there are more breakpoints, which are evenly and logically spaced. To provide more layout possibilities, additional column features have been rolled in that seamlessly integrate with the conventional percentage-based options.

## Features

* Flexbox layout
* Mobile-first methodology
* Concise and intuitive class names
* Logical breakpoints
* No margins, padding, or gutters
* No nesting limitations
* No container requirements
* Ability to hide columns
* Ability to set column width to minimum required
* Ability to set column width to maximum available

## Installation

```
npm install core-grid
```

## Usage

### Grid Basics

A `.row` is a container for columns. By default, a row will occupy the full width of its parent.

A `.col` is a container for content. By default, a column will occupy the maximum amount of space available within its row.

```html
<div class="row">
	<!-- Column is 100% width -->
	<div class="col"></div>
</div>

<div class="row">
	<!-- Columns are 50% width -->
	<div class="col"></div>
	<div class="col"></div>
</div>
```

### Column Width Classes

Rather than sharing the space evenly, columns can each have their own widths set as a percentage of the total width. This is indicated in a class name as the number of columns to occupy out of 12. For example, a column that spans one-quarter of the row occupies 3 columns, and a column that spans two-thirds of the row occupies 8 columns.

The width of a `.col` can also be set to change according to the current window width, which is categorized into 5 sizes, `xs`, `sm`, `md`, `lg`, and `xl`.

When writing column classes, the window width is the prefix and the column width is the suffix. For example, a column that is full-width on mobile devices, and one-half-width on everything larger would be written as `col xs-12 sm-6`. The grid system is mobile-first, so the `xs` style is overridden by the `sm` style, and the `sm` style applies to all larger sizes since it is not overridden by anything itself.

```html
<div class="row">
	<!-- Column width changes according to window width -->
	<div class="col xs-12 sm-6 md-4 lg-3 xl-2"></div>
</div>
```

### Min and Max Column Widths

In addition to the percentage-based suffixes, there are two more: `max`, which will occupy the maximum amount of space that is available (default column behavior), and `min`, which will only occupy the minimum amount of space that it requires.

For example, to create a card component where there is an image on the left and a paragraph on the right, the `min` and `max` behaviors complement each other nicely. The column that contains the image can be set to `min` so that its size is dictated by the image's size, and the column that contains the paragraph can be set to `max` so that it may occupy all the space that is left over.

```html
<div class="row">
	<!-- Min and max used together -->
	<div class="col xs-12 sm-min"></div>
	<div class="col xs-12 sm-max"></div>
</div>
```

### Hiding Columns

A `.col` can be hidden by using a class suffixed with `0`. This applies `display: none` for that window size and larger, unless overridden by another column classes.

```html
<div class="row">
	<!-- Hidden only the smallest size -->
	<div class="col xs-0 sm-6"></div>

	<!-- Hidden only on the largest size -->
	<div class="col xs-6 xl-0"></div>

	<!-- Visible only on the smallest size -->
	<div class="col xs-4 sm-0"></div>

	<!-- Visible only on the largest size -->
	<div class="col xs-0 xl-4"></div>

	<!-- Hidden/visible on alternating sizes -->
	<div class="col xs-12 sm-0 md-12 lg-0 xl-12"></div>
</div>
```

## Reference

### Window Widths

The grid uses logical breakpoints, evenly distributed at 16rem intervals to create a smooth gradation.

| Prefix  | Window Width (em) | Window Width (px) |
| ------- | ----------------- | ----------------- |
| `.xs-*` | >= 0              | >= 0              |
| `.sm-*` | >= 32em           | >= 512px          |
| `.md-*` | >= 48em           | >= 768px          |
| `.lg-*` | >= 64em           | >= 1024px         |
| `.xl-*` | >= 80em           | >= 1280px         |

### Column Widths

The grid uses a 12-column system in order to provide a high level of freedom. Additionally, the `0` suffix hides the column, and the `min` and `max` suffixes provide more situational behavior.

| Suffix   | Column Width            |
| -------- | ----------------------- |
| `.*-0`   | _Hidden_                |
| `.*-1`   | 8.3333%%                |
| `.*-2`   | 16.6667%                |
| `.*-3`   | 25%                     |
| `.*-4`   | 33.3333%                |
| `.*-5`   | 41.6667%                |
| `.*-6`   | 50%                     |
| `.*-7`   | 58.3333%                |
| `.*-8`   | 66.6667%                |
| `.*-9`   | 75%                     |
| `.*-10`  | 83.3333%                |
| `.*-11`  | 91.6667%                |
| `.*-12`  | 100%                    |
| `.*-min` | Minimum space required  |
| `.*-max` | Maximum space available |
