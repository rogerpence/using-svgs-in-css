
## Learning a little about SVG

The Filament Group select tag styling uses this background-image value: 

        background-image: url('data:image/svg+xml;charset=US-ASCII,
            %3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.
            org%2F2000%2Fsvg%22%20width%3D%22292.4%22%20height%3D%22292.
            4%22%3E%3Cpath%20fill%3D%22%23007CB2%22%20d%3D%22M287%2069.4a17.6%2017.
            6%200%200%200-13-5.4H18.4c-5%200-9.3%201.8-12.9%205.4A17.6%2017.
            6%200%200%200%200%2082.2c0%205%201.8%209.3%205.4%2012.9l128%20127.9c3.
            6%203.6%207.8%205.4%2012.8%205.4s9.2-1.8%2012.8-5.4L287%2095c3.5-3.
            5%205.4-7.8%205.4-12.8%200-5-1.9-9.2-5.5-12.8z%22%2F%3E%3C%2Fsvg%3E'),  
            linear-gradient(to bottom, #ffffff 0%, #e5e5e5 100%);
            
> The line above is broken for publication purposes; it should be entered as one entire line in your HTML.

Embedded in this value is an SVG image and a linear gradient. The linear gradient provides the background color. If you want a background color without a gradient make both hex values the same. Don't remove this gradient--it is important to maintain IE compatibility.

The color of the arrow provided by the SVG is embedded in the six characters in the URL between the hex 23 (%23) and hex 22 (%22) values (which is )

    %23007CB2%22

The default color value is 

    007CB2    

and it can be changed to any six-character hex color value.     

### A little more on the SVG

The SVG value above has be URL encoded. Use an [online decoder](https://www.urldecoder.org/) to see its decoded value as shown below:

![](https://rogerpence.com/storage/images/decoding-an-svg.2458680.40177.png)

To edit the image with a vector editor, copy the `svg` tag to a plain text file and open it with your favorite editor. In this example, that leaves this as the `svg` value to edit: 

    <svg xmlns="http://www.w3.org/2000/svg" width="292.4" height="292.4"><path
    fill="#007CB2" d="M287 69.4a17.6 17.6 0 0 0-13-5.4H18.4c-5 0-9.3 1.8-12.9
    5.4A17.6 17.6 0 0 0 0 82.2c0 5 1.8 9.3 5.4 12.9l128 127.9c3.6 3.6 7.8 5.4 12.8
    5.4s9.2-1.8 12.8-5.4L287 95c3.5-3.5 5.4-7.8 5.4-12.8
    0-5-1.9-9.2-5.5-12.8z"/></svg>
    
<small>Figure 1. Raw, decoded SVG from Filament Group CSS</small>    
    

If you do edit the image, respect its original 292.4 x 292.4 size. The Filament Group CSS positions the arrow based on that size.

[figma.com](https://figma.com) and [vectr.com](https://vector.com) are two good online vector editors. Using Chrome, both let you drag and drop the text file for editing. 


### Generating your own background-image SVG url:

If you take the SVG value from Figure 1 above and paste it into [URL-encoder for SVG](https://yoksel.github.io/url-encoder/), you get

    background-image: url("data:image/svg+xml,%3Csvg
    xmlns='http://www.w3.org/2000/svg' viewBox='0 0 292.4 292.4'%3E%3Cpath d='M287
    69.4c-3.4-3.5-8.1-5.5-13-5.4H18.4c-5 0-9.3 1.8-12.9 5.4C2 72.7 0 77.4 0 82.2c0 5
    1.8 9.3 5.4 12.9l128 127.9c3.6 3.6 7.8 5.4 12.8 5.4s9.2-1.8 12.8-5.4L287
    95c3.5-3.5 5.4-7.8 5.4-12.8s-1.9-9.2-5.5-12.8h.1z'
    fill='%23004477'/%3E%3C/svg%3E");
    
which is now directly pasteable into your CSS. 

> Note that URL-encoder for SVG doesn't include a linear-gradient value. You need to add that manually.

### Compressing an SVG 

For SVG's that come directly from Illustrator or Figma, you may want to compress the SVG first with [svgomg](https://jakearchibald.github.io/svgomg/).

    <?xml version="1.0" encoding="utf-8"?>
    <!-- Generator: Adobe Illustrator 23.0.3, SVG Export Plug-In . 
    SVG Version: 6.00 Build 0)  -->
    <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
         viewBox="0 0 292.4 292.4" style="enable-background:new 0 0 292.4 292.4;"
         xml:space="preserve">
        <style type="text/css">
        .st0{fill:#333435;}
        </style>
        <path class="st0" d="M287,69.4c-3.4-3.5-8.1-5.5-13-5.4H18.4c-5,0-9.3,
        1.8-12.9,5.4C2,72.7,0,77.4,0,82.2c0,5,1.8,9.3,5.4,12.9
        l128,127.9c3.6,3.6,7.8,5.4,12.8,5.4s9.2-1.8,12.8-5.4L287,95c3.5-3.5,5.4-7.8,
        5.4-12.8s-1.9-9.2-5.5-12.8L287,69.4z"/>
    </svg>
    
    
You get this compressed SVG:
    
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 292.4 292.4"><path d="M287
    69.4c-3.4-3.5-8.1-5.5-13-5.4H18.4c-5 0-9.3 1.8-12.9 5.4C2 72.7 0 77.4 0 82.2c0 5
    1.8 9.3 5.4 12.9l128 127.9c3.6 3.6 7.8 5.4 12.8 5.4s9.2-1.8 12.8-5.4L287
    95c3.5-3.5 5.4-7.8 5.4-12.8s-1.9-9.2-5.5-12.8h.1z" fill="#333435"/></svg>
    
which can now be pasted into [URL-encoder for SVG](https://yoksel.github.io/url-encoder/) to generate the `background-image` tag value
    