# cairo-c3
A binding of the Cairo graphics library for c3

The binding data was generated with GNOMEs girtools and converted with pyramid. Cairo is a straighforward API with no chain of dependencies, so it was a good case to start with.

This binding attempts to stay as close to the original API as possible. Names are only changed minimally to fit c3's naming conventions, capitialising the first letter and removing the `cairo_` prefix. The only significant change is `cairo_t` which has been renamed to `Context_t`, [as recommended by Cairo 's developers](https://www.cairographics.org/manual/language-bindings.html).

All functions are module level and not written as methods. There will soon be a more c3 structured Cairo binding, where most functions are bound as methods of Cairo types.

## Install

Simply clone this repo. There is only one file, compile it along with any other source files and link to Cairo. The module is named 'cairo'. Use Cairo as you would normally.

### Example code
```
fn bool draw (cairo::Context_t* ctx) {
	cairo::arc (ctx, 0, 0, 16, 3, 4);
	cairo::set_line_width (ctx, 3.0);
	cairo::set_source_rgba (ctx, 1.0, 0.5, 0.5, 1.0);
	cairo::stroke (ctx);
	cairo::arc (ctx, 0, 0, 28, 3, 4);
	cairo::stroke (ctx);
    
	cairo::set_line_width (ctx, 8.0);
	cairo::set_source_rgba (ctx, 0.5, 1.0, 0.5, 0.9);
	cairo::move_to (ctx, -12, 20);
	cairo::line_to (ctx, -12, -20);
	cairo::move_to (ctx, 12, 20);
	cairo::line_to (ctx, 12, -20);
	cairo::set_line_width (ctx, 12.0);
	cairo::stroke (ctx);
}
