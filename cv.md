# Daria Chepikova
*Web developer*

![Photo](https://d1bvpoagx8hqbg.cloudfront.net/259/3d6d384490bbc26ce03491a6893eeaf5.jpg)


## Summary
At the moment I am a 4th year student of State Technical University P.O.Sukhoi as programmer and I have no work experience in programming. I'm trying to improve my English. I have knowledge of Photoshop. I like to learn something new.

## Skills

HTML/CSS/JavaScript, C++, C#, Git

## Code examples

```
var DragManager = new function() {
    var dragObject = {};

    var self = this;

    function onMouseDown(e) {

        if (e.which != 1) return;

        var elem = e.target.closest('.paper');
        if (!elem) return;

        dragObject.elem = elem;

        dragObject.downX = e.pageX;
        dragObject.downY = e.pageY;

        return false;
    }

    function openContainer() {
        let Container = document.getElementsByClassName('Container');
        let ContainerOpen = document.getElementsByClassName('ContainerOpen');
        Container[0].style.visibility = 'visible';
        ContainerOpen[0].style.visibility = 'hidden';
    }

    function Schetchik() {
        let pic = document.getElementById("pic");
        let img = pic.querySelectorAll("img");
        document.getElementById("sch").style = "margin-left: 100px; color: red;";
        document.getElementById("sch").innerHTML = "Осталось " + img.length + " бумажек.";
    }

    function closeContainer() {
        let Container = document.getElementsByClassName('Container');
        let ContainerOpen = document.getElementsByClassName('ContainerOpen');
        Container[0].style.visibility = 'hidden';
        ContainerOpen[0].style.visibility = 'visible';
    }

    function onMouseMove(e) {
        if (!dragObject.elem) return;

        if (!dragObject.avatar) {
            var moveX = e.pageX - dragObject.downX;
            var moveY = e.pageY - dragObject.downY;
            if (Math.abs(moveX) < 3 && Math.abs(moveY) < 3) {
                return;
            }
            dragObject.avatar = createAvatar(e);
            if (!dragObject.avatar) {
                dragObject = {};
                return;
            }
            var coords = getCoords(dragObject.avatar);
            dragObject.shiftX = dragObject.downX - coords.left;
            dragObject.shiftY = dragObject.downY - coords.top;
            startDrag(e);
        }

        let flag = false;
        let a = e.pageX - dragObject.shiftX;
        let b = e.pageY - dragObject.shiftY;
        dragObject.avatar.style.left = e.pageX - dragObject.shiftX + 'px';
        dragObject.avatar.style.top = e.pageY - dragObject.shiftY + 'px';
        let Container = document.getElementsByClassName('Container');
        if (a >= Container[0].width - 100 && a <= Container[0].width + 100 && b >= 100 && b <= 200 && flag == false) {
            openContainer();
            flag = true;
        } else {
            closeContainer();
            flag = false;
        }
        return false;
    }
    var count = 0;

    function onMouseUp(e) {
        if (dragObject.avatar) {
            let Container = document.getElementsByClassName('Container');
            let a = e.pageX - dragObject.shiftX;
            let b = e.pageY - dragObject.shiftY;
            if (a >= Container[0].width - 100 && a <= Container[0].width + 100 && b >= 100 && b <= 200) {
                dragObject.elem.hidden = true;
                dragObject.elem.style.visibility = 'hidden';
                Schetchik();
                closeContainer();
                count++;
            }
            finishDrag(e);
        }
        dragObject = {};
    }

    function finishDrag(e) {
        var dropElem = findDroppable(e);

        if (!dropElem) self.onDragCancel(dragObject);

        else self.onDragEnd(dragObject, dropElem);
    }

    function createAvatar(e) {
        var avatar = dragObject.elem;
        var old = {
            parent: avatar.parentNode,
            nextSibling: avatar.nextSibling,
            position: avatar.position || '',
            left: avatar.left || '',
            top: avatar.top || '',
            zIndex: avatar.zIndex || ''
        };

        avatar.rollback = function() {
            old.parent.insertBefore(avatar, old.nextSibling);
            avatar.style.position = old.position;
            avatar.style.left = old.left;
            avatar.style.top = old.top;
            avatar.style.zIndex = old.zIndex
        };

        return avatar;
    }

    function startDrag(e) {
        var avatar = dragObject.avatar;
        document.body.appendChild(avatar);
        avatar.style.zIndex = 9999;
        avatar.style.position = 'absolute';
    }

    function findDroppable(event) {
        dragObject.avatar.hidden = true;
        var elem = document.elementFromPoint(event.clientX, event.clientY);
        dragObject.avatar.hidden = false;

        if (elem == null)
            return null;
        return elem.closest('.bag');
    }

    document.onmousemove = onMouseMove;
    document.onmouseup = onMouseUp;
    document.onmousedown = onMouseDown;

    this.onDragEnd = function(dragObject, dropElem) {};
    this.onDragCancel = function(dragObject) {};
};

function getCoords(elem) {
    var box = elem.getBoundingClientRect();

    return {
        top: box.top + pageYOffset,
        left: box.left + pageXOffset
    };
}
```

## Work experience

Completed external courses in front-end development at EPAM. I have done various projects within the University: made apps for composing new dishes, as well as for ordering them.

## Education

I am a 4th year student of State Technical University P.O.Sukhoi as a systems programmer. Completed external courses in front-end development at EPAM. Now I take courses at RSSchool.

## English

My English level is B1. I practice spoken and written English with foreign friends. Sometimes I watch movies in English.