# WordPress-Gallery-Pop-Up-JS

```JavaScript
<script>
(function($) {
    var file_frame;
    $("#well").on("click", function(event) {
        event.preventDefault();
        if (file_frame) {
            file_frame.open();
            return;
        }
        // Create the media frame.
        file_frame = wp.media.frames.file_frame = wp.media({
            title: $(this).data("File upload"),
            button: {
                text: $(this).data("Upload")
            },
            multiple: false // Set to true to allow multiple files to be selected
        });
        // When an image is selected, run a callback.
        file_frame.on("select", function() {
            // We set multiple to false so only get one image from the uploader
            attachment = file_frame.state().get("selection").first().toJSON();
            // $("#csv_file").attr("value", attachment.url);
            console.log(attachment);
        });

        // Finally, open the modal
        file_frame.open();
    });
})(jQuery);
</script>

```
