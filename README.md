# GTNH Uncertainty Resolver Solver

A single-page web tool for the TecTech Quantum Computer's Uncertainty Resolver in GT New Horizons. Drop, paste or pick a screenshot of the resolver GUI, and it lists which swap buttons to press, in order, to turn every LED green.

**Use it:** https://maselkov.github.io/gtnh-uncertainty-solver/

## How it works

- **Reading the screenshot:** each matrix cell is drawn as `#0073ff` blue over black, with opacity set to value / 1000. The page finds the matrix frame, then reads each cell's value from its blue level. The value-assist numbers can be on or off. Active LEDs are found by colour, and they determine the LED layout.
- **Rules:** these match `MTEHatchUncertainty.compute()` in [GT5-Unofficial](https://github.com/GTNewHorizons/GT5-Unofficial). Each active LED checks a group of cells. Cells mirrored through the LED form pairs, and the LED is green when the summed pair differences are below 128 × the group size.
- **Solving:** the page tries every sequence of 1, 2 or 3 swaps and keeps the one with the most headroom. It plans with a small safety margin to absorb rounding in the screenshot. If no short sequence works, it falls back to simulated annealing.

## Tips

- After opening the GUI, wait for the LEDs to appear before you take the screenshot. They can take a few seconds.
- Use PNG screenshots (F2). Any GUI scale works.
- If a cell is misread, type the correct value into the grid.

Everything runs in the browser. Screenshots are never uploaded.

## License

GPL-3.0. See [LICENSE](LICENSE).
