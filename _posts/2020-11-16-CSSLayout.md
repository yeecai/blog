2020-11-16-CSSLayout



1. Fullscreen layout

   [<img src="{{ site.baseurl }}/images/layout/image-20201116173429399.png" alt="Fullscreen layout" style="width: 400px;"/>]({{ site.baseurl }}/)

   code:

```html
<div class="fullscreen-layout">
	<header></header>
    <main><aside></aside></main>
    <footer></footer>
</div>
```

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
        left: 0;
        top: 50px;
        bottom: 50px;
        width: 50px;
		background-color: #39C;
    }
}
```



2.  Two columns:

   Left column with fixed width, the right column fits the rest, and two columns same height.

   ![两列布局](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1c9804b4659f4f42ad11463ae49bdb8e~tplv-k3u1fbpfcp-zoom-1.image)

   code: 

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

   use margin or padding or flexbox to create.

   ```html
   <div class="grail-layout">
       <div class="left"></div>
       <div class="right"></div>
       <div class="center"></div>
   </div>
   ```

   flex:

   ```
   .grail-layout {
       display: flex;
       width: 400px;
       height: 400px;
       .left {
           width: 100px;
           background-color: #f66;
       }
       .center {
           flex: 1;
           background-color: #3c9;
       }
       .right {
           width: 100px;
           background-color: #66f;
       }
   }
   ```

   

   

   margin：

   ```css
   
   ```

   padding：

   ```css
   
   ```

   

   

Picture and source code referred from [玩转CSS的艺术之美](https://juejin.im/book/6850413616484040711)

[Codepen demo](https://codepen.io/liliancai/pen/ExyMNLa?__cf_chl_jschl_tk__=80cadff6a5569f507708827b07c7cab897bf45b8-1605518229-0-AdGxsLS0RJfBqjdvPTRHTr8mM7Z2KG3CfAi4a7QVvSi3j0uswYtS7lnLe-D7qjJ68LaCg_0TV7BgZi0co5wU70qKBV9Yq-NecMuQQqyzJJIcy8bN3vupPSRNLTzI9FFV0NJcxNyAN9GjhoBplbMcvxAR1Vilu126Hp39-Y02y95GX6EgUvQYJc2dxcgzpHoofAky7gFI8BxC-c6_RawUuMOzQ-wDR0S8q5MElFLWrEw9-ltM73pLtBd4Uy5XbAAfGNRKbKJ_VnEu5LRZ5l6HdDCDfyVUars9upJCg-4XToJCdH-ekPNqkNgkRaxWXGIa4n5yDXrHW9nqa_qs9TN5cNuKlWBP_uLJ3d_55eVB_rJL)