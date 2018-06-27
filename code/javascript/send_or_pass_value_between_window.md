# Send/Pass value of child window to parent window


We can use `window.opener` to call parent window from child window.

```
<head>
  <script language=”javascript” type=”text/javascript”>
    function SendValueToParent() {
      var myVal = document.getElementById(‘mytxt’).value;
      window.opener.GetValueFromChild(myVal);
      window.close();
      return false;
    }
  </script>
</head>



<body>
  Type text here and send it to parent window:
  <input id=”mytxt” type=”text” />
  <input id=”btn1″ type=”button” value=”Send Value to Parent” onclick=”javascript:return SendValueToParent();” />
</body>
```
