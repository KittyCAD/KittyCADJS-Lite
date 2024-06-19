# KittyCAD.js Lite

A custom KittyCAD API JS client which is manually maintained and does not follow
the OpenAPI updates.

## Usage

Either include the `index.js` in a `<script></script>` or use
`<script src="./index.js"></script>` to have access to the `KittyCADClient`
class.

Initializating and usage is easy:

```
  KittyCADClient("API TOKEN", () => {
    // You can now use any modeling command here!
    // Check the documentation for what's available:
    // https://zoo.dev/docs/api/modeling/open-a-websocket-which-accepts-modeling-commands?lang=rust#parameters-body-modeling_cmd_req-cmd

    // Example, that doesn't actually work, but what modeling commands
    // look like:
    default_camera_zoom({ magnitude: -25 });
    default_camera_look_at({
      center: { x: 0, y: 0, z: 0 },
      up: { x: 0, y: 0, z: 1 },
      vantage: { x: 0, y: -100, z: 75 },
    });
    const plane_id = make_plane({
      clobber: false,
      hide: true,
      origin: { x: 0, y: 0, z: 0 },
      size:  1,
      x_axis: {x: 1, y: 0, z: 0},
      y_axis: {x: 0, y: 1, z: 0},
    });
    enable_sketch_mode({
      entity_id: plane_id,
      ortho: false,
      animated: false,
      adjust_camera: false,
    });
    const path = start_path();
    move_path_pen({ path, to: { x: 0, y: 0, z: 0 }});
    extend_path({
      path,
      segment: {
        type: "line",
        end: { x, y, z: 0 },
        relative: false,
      }
    });
    close_path({ path_id: path });
    sketch_mode_disable();

    done();
  })
```
