

1. **Full-screen layout**

   Header, footer with a fixed height, and the main stretch the rest height. 

   [<img src="{{ site.baseurl }}/images/layout/image-20201116173429399.png" alt="Fullscreen layout" style="width: 400px;"/>]({{ site.baseurl }}/)

```html
<div class="fullscreen-layout">
	<header></header>
    <main><aside></aside></main>
    <footer></footer>
</div>
```

absolute+

```scss
.fullscreen-layout {
    position: relative;
    width: 400px;
    height: 400px;
    header, main, footer {
        position: absolute;
        left: 0;
        right: 0;
    }
    header {
        top: 0;
        height: 50px;
        background-color: #F66;
    }
    footer {
        bottom: 0;
        height: 50px;
        background-color: #66F;
    }
    main {
        top: 50px;
        bottom: 50px;
        background-color: #3C9;
    }
    aside {
		height: 100%;
		width: 100px;
		background-color: #39C;
	}
}
```



2.  **Two columns**

   Left column with fixed width, the right column fits the rest, and two columns same height.

   ![两列布局](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1c9804b4659f4f42ad11463ae49bdb8e~tplv-k3u1fbpfcp-zoom-1.image)

   ```html
<div class="two-column-layout">
   	<div class="left"></div>
       <div class='right'></div>
   </div>
   ```
   
   ```scss
.two-column-layout {
       width: 400px;
       height: 400px;
       .left, .right {
           height: 100%;
       }
       .left {
           left: 0;
           width: 100px;
           background-color: #F66;
       }
       .right {
           margin-left: 100px;
           background-color: #66F;
       }
   }
   
   // flex version
   .two-column-layout {
       display: flex;
       width: 400px;
       height: 400px;
       .left {
           width: 100px;
           background-color: #F66;
       }
       .right {
           flex: 1;
           background-color: #66F;
       }
   }
   ```
   
   

3. Three columns layout

   the basic method is float+overflow or flexbox

   ![三列布局](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/abcc731db88b464ca6b91c66fe38b9a2~tplv-k3u1fbpfcp-zoom-1.image)

code

```html
<div class="three-column-layout">
    <div class="left"></div>
    <div class="center"></div>
    <div class="right"></div>
</div>
```



```scss
.three-column-layout {
	width: 400px;
	height: 400px;
	.left, right, center {
		height: 100%;
	}
	.left {
		float: left;
		width: 50px;
		background-color: #F66;
	}
	.center {
		float: left;
		width: 100px;
		background-color: #66F;
	}
	.right {
		overflow: hidden;
		background-color: #3C9;
	}
}

// flex
.three-column-layout {
    display: flex;
	width: 400px;
	height: 400px;
	.left, right, center {
		height: 100%;
	}
	.left {
		width: 50px;
		background-color: #F66;
	}
	.center {
		width: 100px;
		background-color: #66F;
	}
	.right {
        flex: 1;
		background-color: #3C9;
	}
}
```



4. Grail-layout 

   Can use margin or padding or flexbox to create holy grail layout.

   ```html
   <div class="grail-layout">
       <div class="left"></div>
       <div class="center"></div>
       <div class="right"></div>
   </div>
   ```

   flex:

   ```css
   .grail-layout {
       display: flex;
       width: 400px;
       height: 400px;
       .left {
           width: 100px;
           background-color: #F66;
       }
       .center {
           flex: 1;
           background-color: #3C9;
       }
       .right {
           width: 100px;
           background-color: #66F;
       }
   }
   ```

   

   padding:

   We need move the right div in front of the center div otherwise the right one would sink to a new line.

   ```
   <div class="grail-layout">
       <div class="left"></div>
    <div class="center"></div>
       <div class="right"></div>
</div>
   ```
   
   

   ```css
.grail-layout {
       padding: 0 100px;
       width: 400px;
       height: 400px;
       .left, .right, .center {
   		height: 100%;
   	}
   	.left, .right {
   		width: 100px;
   	}
       .left {
           float: left;
           margin-left: -100px;
           background-color: #F66;
       }
       .right {
           float: right;
           margin-right: -100px;
           background-color: #66F;
       }
       .center {
           background-color: #3C9;
       }
   }
   ```
   
   margin + float: 
   
   the html code same with above and same reason, float element need to put before the non-float element in the same line.
   
   ```css
   .grail-layout {
       .left, .right, .center {
   		height: 100%;
   	}
       .left, .right {
           width: 100px;
       }
       .left {
           float: left;
           background-color: #F66;
       }
       .right {
           float: right;
           background-color: #66F;
       }
       .center {
           margin: 0 100px;
           background-color: #3C9;
       }
   }
   ```
   
   
   
   5. Average layout
   
      Each one equally split the width.
   
      ````html
      <div class="average-layout">
          <div class="one"></div>
          <div class="two"></div>
          <div class="three"></div>
          <div class="four"></div>
      </div>
      ````
   
      solution1: flex = 1
   
      ```scss
      .average-layout {
      	display: flex;
          width: 400px;
          height: 400px;
      	div {
      		flex: 1;
              border-left: 1px solid pink;
      	}
      }
      ```
   
      solution2:  float + width
   
      ```scss
      .average-layout {
      	display: flex;
          width: 400px;
          height: 400px;
      	div {
              float: right;
              width: calc(100% / 4);
              border-left: 1px solid pink;
      	}
      }
      ```
   
      solution3: 
   
      ```scss
      .average-layout {
          column-count: 4;
          column-gap: 0;
          width: 400px;
          height: 400px;
          div {
              height: 100%;
          }
      }
      ```

Picture and source code referred from [玩转CSS的艺术之美](https://juejin.im/book/6850413616484040711)

[Codepen demo](https://codepen.io/liliancai/pen/ExyMNLa?__cf_chl_jschl_tk__=80cadff6a5569f507708827b07c7cab897bf45b8-1605518229-0-AdGxsLS0RJfBqjdvPTRHTr8mM7Z2KG3CfAi4a7QVvSi3j0uswYtS7lnLe-D7qjJ68LaCg_0TV7BgZi0co5wU70qKBV9Yq-NecMuQQqyzJJIcy8bN3vupPSRNLTzI9FFV0NJcxNyAN9GjhoBplbMcvxAR1Vilu126Hp39-Y02y95GX6EgUvQYJc2dxcgzpHoofAky7gFI8BxC-c6_RawUuMOzQ-wDR0S8q5MElFLWrEw9-ltM73pLtBd4Uy5XbAAfGNRKbKJ_VnEu5LRZ5l6HdDCDfyVUars9upJCg-4XToJCdH-ekPNqkNgkRaxWXGIa4n5yDXrHW9nqa_qs9TN5cNuKlWBP_uLJ3d_55eVB_rJL)