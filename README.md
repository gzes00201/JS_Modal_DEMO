# JS_Modal_DEMO

DEMO:
http://htmlpreview.github.io/?https://github.com/gzes00201/JS_Modal_DEMO/blob/master/demo.html

純粹用JS 達成Modal的效果

####################################### HTML說明 #######################################
結構

Modal開啟的按鈕 使用class="modal_Btn"來監聽 並用data-target="myModal" 標註開啟內容
範例:<button class="modal_Btn" data-target="myModal">訊息1</button>



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

本範例JS第二區塊綁定關閉事件，透過.modal綁定
先把迴圈當下的自己id存起來
var myid=close[index].getAttribute('id');
並取得本div底下的第一個.close
var close_span=close[index].getElementsByClassName('close')[0];
綁定點選.close後，id是myid的物件(就是本DIV)會關閉
document.getElementById(myid).style.display = "none";

第三部分 綁定點選空白處modal關閉

第四部分，因為內容區塊.modal-content 是被第三部分的.modal包覆
因此當點選.modal-content的時候透過event.preventDefault();event.stopPropagation();來阻止
.modal的關閉動作
