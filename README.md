# Math-HTML-JS-progress-bar
progress bar with function to fill completed tasks , this can uses to calclate smallest number until 1e-323%, so if the task is in stage 1e-323% it will not say it 0 and will display that in prorgess bar what means it can handle any dividing of large tasks bar no usally pc or rocket system have this tasks number.


![image](https://github.com/MahmoudHegazi/Math-HTML-JS-progress-bar/assets/55125302/19494057-32c7-4e3a-b8ae-d2173770567c)

example it also tells you what fixed number fixed this number eg: ```parseFloat(0.00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000012111).toFixed(97);``` 1e-97, and will continue up until 1e-99
![image](https://github.com/MahmoudHegazi/Math-HTML-JS-progress-bar/assets/55125302/7d275d19-0f10-402f-86f2-bfe69f5647b5)

and down also, so user will have the accurest smallest number of task done in system contains 0.99 deciemal and reflext in result(dynamic select fixed 
![image](https://github.com/MahmoudHegazi/Math-HTML-JS-progress-bar/assets/55125302/16a77293-088a-4f1b-afc1-abe9d3e01e40)


eg 12555 tasks done from 151515151:
![image](https://github.com/MahmoudHegazi/Math-HTML-JS-progress-bar/assets/55125302/a793b0ac-4ec3-4125-bad1-71b38e4a0c3c)

![image](https://github.com/MahmoudHegazi/Math-HTML-JS-progress-bar/assets/55125302/ce2d775f-539a-4dee-9c6a-9032f7161a65)



# first version

```
function updateMathSkillBar(stepsDone=0, maxSteps=0, selector='.categories_blancer_bar'){

    if (!selector || !$(selector).length){
        console.warn("Please Provide range selector");
        return false;
    }

    if (
        isNaN(parseInt(stepsDone)) || isNaN(parseInt(maxSteps)) ||
        typeof(parseInt(stepsDone)) !== 'number' || typeof(parseInt(maxSteps)) !== 'number') {

        if (typeof(selector) !== 'undefined' && $(selector).length) {
            $(selector).css("width", "0%");
            $(selector).text("0%");
        }
        console.warn("Please Provide valid numbers totalSteps and maxSteps");
        return false;
    }
    if (stepsDone > maxSteps) {
        console.warn("total steps can not be more than max steps");
        return false;
    }
    // handle divide on zero case
    if (maxSteps > 0) {
        let precentage = parseFloat(stepsDone) / parseInt(maxSteps) * 100;
        precentage = (parseFloat(precentage) === precentage) ? (precentage).toFixed(1) : precentage;
        console.log(precentage);
        // fixed calc result
        if (parseFloat(precentage) == parseInt(precentage)) {

            precentage = Math.round(precentage);
        }
        $(selector).css('width', `${precentage}%`);
        $(selector).text(`${precentage}%`);
    } else {
        $(selector).css('width', '0%');
        $(selector).text('0%');
        console.warn("divde buy zero handle");
    }
}

```
