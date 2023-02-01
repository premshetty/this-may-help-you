### Thought of creating a file that can solve many minute problem that are small
- ---
# JavaScript One line Code to Check If it's  a Mobile Screen or not

<code>
  const isMobile = () => window.matchMedia('(max-width: 700px)').matches
  </code>
<hr />

# how to add background image to next js 
```
style={{
        backgroundImage: 'url("/beach.avif")',
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }}
```
# print a particular div 

```js

function PrintElem(elem)
{
    var mywindow = window.open('', 'PRINT', 'height=400,width=600');

    mywindow.document.write('<html><head><title>' + document.title  + '</title>');
    mywindow.document.write('</head><body >');
    mywindow.document.write('<h1>' + document.title  + '</h1>');
    mywindow.document.write(document.getElementById(elem).innerHTML);
    mywindow.document.write('</body></html>');

    mywindow.document.close(); // necessary for IE >= 10
    mywindow.focus(); // necessary for IE >= 10*/

    mywindow.print();


    return true;
}

PrintElem('print1')

```
