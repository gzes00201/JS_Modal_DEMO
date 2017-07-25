# JS_Modal_DEMO

DEMO:
http://htmlpreview.github.io/?https://github.com/gzes00201/JS_Modal_DEMO/blob/master/demo.html

純粹用JS 達成Modal的效果

####################################### HTML說明 #######################################
結構

Modal開啟的按鈕 使用class="modal_Btn"來監聽 並用data-target="myModal" 標註開啟內容
範例:
<pre><code>This is a regular paragraph.

&lt;table&gt;
    &lt;tr&gt;
        &lt;td&gt;Foo&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;

This is another regular paragraph.
</code></pre>
<code><button class="modal_Btn" data-target="myModal">訊息1</button></code>

開啟內容id="myModal"標註被開啟的，並用class="modal"告知此為Modal內容，裡面的 class="close"是關閉按鈕，不一定要用span
範例:"
<div id="myModal" class="modal">
  <div class="modal-content">
    <span class="close">&times;</span>
    <p>顯示訊息1</p>
  </div>
</div>
"
####################################### JS說明 #######################################
本範例用JS撰寫，因此內容與JQUERY比較起來會比較繁雜

首先
綁定開啟事件 透過CLASS
var modal = document.getElementsByClassName('modal_Btn');

JS的CLASS選擇器會傳回陣列，所以用FOR去設定每一個.modal_Btn，陣列從0開始
因此要跑 0~ modal.length(陣列長度)

監聽設置方法是modal[index].addEventListener("click", function() { });

以下範例是把
CLASS為modal_Btn的data-target取出
並綁定當自己被點選後，ID為data-target的style.display被block

for(var i = 0; i < modal.length; i++) {
  (function(index) {
    modal[index].addEventListener("click", function() { 
       document.getElementById(this.getAttribute("data-target")).style.display = "block";       
     })
  })(i);
}
