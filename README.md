# Interactive Color Picker

A simple, single-file web application that allows users to pick colors using RGB sliders and view the corresponding hexadecimal output in real-time. This minimalist project demonstrates interactive UI elements using only HTML and vanilla JavaScript.

## How to Use

1.  **Save the file:** Save the provided `index.html` content into a file named `index.html` on your local machine.
2.  **Open in browser:** Open the `index.html` file using any modern web browser (e.g., Chrome, Firefox, Safari, Edge).
3.  **Adjust sliders:** Interact with the Red, Green, and Blue sliders to change the color. Each slider controls the intensity of its respective color component from 0 to 255.
4.  **View output:** The large `Color Preview` box will update with the selected color, and the `Hex Output` below it will display the corresponding hexadecimal color code. You can easily copy the hex code from this output.

## Code Explanation

This project is entirely contained within a single `index.html` file, embracing a minimalist approach to web development.

*   **HTML Structure (`<body>`):**
    *   A central `div` with the class `color-picker-container` acts as the main wrapper for the application, providing a clean layout.
    *   Three separate `div.slider-group` elements are used for Red, Green, and Blue. Each group contains:
        *   A `<label>` (R, G, B) for accessibility and identification.
        *   An `<input type="range">` slider (`id="redSlider"`, etc.) with `min="0"` and `max="255"` for color component values.
        *   A `<span>` (`id="redValue"`, etc.) to display the current numeric value of its respective slider.
    *   A `div.color-preview` element (`id="colorBox"`) visually represents the currently selected color.
    *   A `div.hex-output` element (`id="hexOutput"`) displays the computed hexadecimal color code.

*   **CSS Styling (`<style>` in `<head>`):**
    *   The CSS provides a modern and clean aesthetic. It uses Flexbox for easy centering of the main container.
    *   Custom styles are applied to the range input sliders, including distinct thumb colors for Red, Green, and Blue, enhancing usability and visual feedback.
    *   Styles ensure the color preview and hex output are clearly visible and well-formatted.

*   **JavaScript Logic (`<script>` in `<body>`):**
    *   **DOM Element Selection:** All necessary HTML elements (sliders, value displays, color box, hex output) are selected and stored in constants using `document.getElementById()`.
    *   **`componentToHex(c)` Function:** This utility function takes a single color component (0-255) and converts it into its two-digit hexadecimal representation. It prepends a '0' if the hex value is a single digit (e.g., `10` becomes `0A`, `255` becomes `FF`).
    *   **`rgbToHex(r, g, b)` Function:** This function takes the three integer RGB values and uses `componentToHex` to combine them into a full 6-digit hexadecimal color string, prefixed with `#`.
    *   **`updateColor()` Function:** This is the core logic function.
        1.  It reads the current `value` from each of the three RGB sliders.
        2.  It updates the `textContent` of the corresponding `<span>` elements to show the numeric RGB values.
        3.  It constructs an `rgb()` CSS string (e.g., `rgb(255, 0, 128)`) and applies it to the `background-color` style of the `colorBox`.
        4.  It calls `rgbToHex` with the current RGB values to get the hexadecimal string.
        5.  Finally, it updates the `textContent` of the `hexOutput` element with the uppercase hexadecimal color code.
    *   **Event Listeners:** An `input` event listener is attached to each slider. Every time a slider's value changes, the `updateColor()` function is executed, ensuring real-time updates.
    *   **Initialization:** `updateColor()` is called once when the script loads (`<script>` at the end of `<body>`) to set the initial state of the color picker, defaulting to black (`#000000`).

## License

This project is licensed under the MIT License.