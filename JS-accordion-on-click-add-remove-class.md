# Example 1
```JS
var elements = document.getElementsByClassName("accordion");
for (var i = 0; i < elements.length; i++) {

    elements[i].addEventListener('click', function() {

        if( this.nextElementSibling.classList.contains("rs-acc-open") ) {

            this.nextElementSibling.classList.remove("rs-acc-open");
        } else {

            this.nextElementSibling.classList.add("rs-acc-open");
        }
    });
}
```

# Example 2
```JS
var elemBtn = document.getElementsByClassName("more");
for (var i = 0; i < elemBtn.length; i++) {

    elemBtn[i].addEventListener('click', function() {

        var elemCom = this.parentNode.previousElementSibling.getElementsByClassName("complete");
        if ( elemCom[0].classList.contains("rs-dis-blo") ) {

            elemCom[0].classList.remove("rs-dis-blo");
        } else {

            elemCom[0].classList.add("rs-dis-blo");
        }
    })
}
```
