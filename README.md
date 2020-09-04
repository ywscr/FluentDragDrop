# Fluent Drag&Drop

Drag&Drop in WinForms is cumbersome and error-prone. There are multiple events to handle and properties to set on at least two controls. Passing data is ... interesting ... and you don't get preview images while dragging things aroud.

Wouldn't it be great if you could use Drag&Drop with fluent code like this?

```
private void pic1_MouseDown(object sender, MouseEventArgs e)
{
    pic1.StartDragAndDrop()
        .WithData(pic1.Image)                                     // pass any object you like
        .WithPreview(img => Watermark(img)).RelativeToCursor()    // define your preview and how it should behave
        .To(pic2, (target, data) => target.Image = data)          // use your data after it was dropped (with type safety)
        .Copy();                                                  // Copy(), Move() or Link() to define allowed effects
}
```
It's all in there: Putting data to the drag&drop operation, attaching a custom preview image to the mouse cursor, working with the dragged data once it's dropped and more.

![Screenshot](doc/4.gif)

Other presets:

![Screenshot](doc/1.gif)

![Screenshot](doc/2.gif)

![Screenshot](doc/3.gif)
