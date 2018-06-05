# Js-checkbox
本章是使用js来实现简单的checkbox选择框的联动
# 当点击全选checkbox时：
我们知道此时所对应的所有checkbox的值都应该是true,状态显示为已选择
# 当所有checkbox都选择时：
当我们把所有checkbox都选择时(值都为true)时,对应我们之前的全选checkbox的值也应为true,状态显示为已选择
# Code
    全部:
    <input type="checkbox" id="ok">
    <hr />
    <div id="obox">
        <input type="checkbox">
        <input type="checkbox">
        <input type="checkbox">
        <input type="checkbox">
    </div>
    当我们点击id为ok的checkbox时,id为obox的div中的所有checkbox都应该为true
    所以我们首先通过js来实现这一简单的功能：
    // window.onload这样就可以通过js代码直接定义这个方法，而不需要象这样定义了<body onload="aaa()"> 
    window.onload=function(){
    //获取对象
        var oBtn = document.getElementById('ok');
        var oBox = document.getElementById('obox');
        var aCh  = oBox.getElementsByTagName('input');
    //设置全选checkbox的点击事件
        oBtn.onclick=function(){
            if(this.checked==true){
                for(var i = 0; i< aCh.length; i++){
                   aCh[i].checked=true;
                 }
            }else{
                for(var i = 0; i< aCh.length; i++){
                    aCh[i].checked=false;
                }
            }
        };
    当id为obox的div中的所有checkbox的值都为true时,id为ok的checkbox全选框值也变为true
    //设置div中所有checkbox的点击事件
    for(var i = 0; i< aCh.length; i++){
         aCh[i].onclick=function(){
        //设置一个变量 用来统计div中checked值为true的个数
            var n = 0;
            for(var i = 0; i< aCh.length; i++){
                if(aCh[i].checked==true){
                    n++;
                }
            }
        //当n的值与div中checked值为true的个数相当时候
            if(n==aCh.length){
            //将全选checked赋值为true
                oBtn.checked=true;
            }else{
                oBtn.checked=false;
            }
        }
      }
# 小结
通过js中的for及if判断来不断的给checked赋值,从而达到我们所有的效果
本章为js实现checked的联动
