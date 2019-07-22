# Heat-Map

*A simple d3 heat map*

This is an app that provides you with a template to make a heat map.



...

**Home Page**

<img src="/HeatMap.PNG" title="home page" alt="home page" width="500px">


---


## Table of Contents 

> Sections
- [Sample Code](#Sample_Code)
- [Installation](#installation)
- [Features](#features)
- [Contributing](#contributing)
- [Team](#team)
- [FAQ](#faq)
- [Support](#support)
- [License](#license)


---

## Sample Code

```javascript
// heat map
var h= 450;
var w= 1350;    
    
const xScale= d3.scaleLinear()
                .domain([1753,2015])
                .range([100,w-30]);
    
const yScale= d3.scaleLinear()
                .domain([0,11])
                .range([50,h-100]);

const toolTip = d3.select('body')
                  .append('div')
                  .attr("id","tooltip")
                  .style("opacity",0);
    
const svg = d3.select('body')    
              .append('svg')
              .attr("height",h)
              .attr("width",w);
     
      svg.selectAll('rect')
         .data(json['monthlyVariance'])
         .enter()
         .append('rect')
         .attr("x",(f,i)=>xScale(f["year"]))
         .attr("y",(f,i)=>yScale(f["month"]-1))
         .attr("width",5)
         .attr("height",27)
         .attr("fill",(f,i)=>f["color"])
         .attr("class","cell")
         .attr("data-month",(f,i)=>f["month"]-1)
         .attr("data-year",(f)=>f["year"])
         .attr("data-temp",(f,i)=>f["dataTemp"])
         .on("mouseover", function(par){
            toolTip.transition()
                   .duration(200)
                   .style("opacity", 0.7);
            toolTip.attr('data-year',d3.select(this).attr('data-year')); 
            toolTip.html(par.dataMonth + " - " + par.year + "<br />" + par.dataTemp.toFixed(1) +"&degC" +"<br />" + par.variance.toFixed(1)+"&degC")
                   .style("left",d3.event.pageX + 10 + "px")
                   .style("top",d3.event.pageY + 10 +"px");
         })           
         .on("mouseout", function(par){
            toolTip.transition()
                   .style("opacity",0)
         });
    
    const xAxis= d3.axisBottom(xScale).tickFormat(d3.format(".0f"));
    const yAxisFormat = function(par) {
      const month = d3.timeParse('%m')(par + 1);
      return d3.timeFormat('%B')(month);
    }
    let yAxis = d3.axisLeft(yScale).tickFormat(yAxisFormat);
    
    var colorArray=["#8b1e06","red","#DA541D","#F69c40","#F4C732","#F9EE5D","#A8EEF9", "#79E4F5","#4BCEE3", "#1DADC4", "#04869B"]; colorArray= colorArray.reverse();
    var textArray=["2.8","3.9","5.0","6.1","7.2","8.3","9.5","10.6","11.7", "12.8"];
    
const legend = svg.selectAll('.legend')
                  .data(colorArray)
                  .enter()
                  .append('g')
                  .attr('id','legend')
                  .attr("transform", "translate(100,350)");  
          
    legend.append('rect')
          .attr('width', 30)                         
          .attr('height', 25)
          .attr("x", (f,i)=>i*30)
          .attr("y", 55)
          .style('fill', (f)=>f)
          .style('stroke', "black");

const legend2 = svg.selectAll('.legend')
                  .data(textArray)
                  .enter()
                  .append('g')
                  .attr('id','legend')
                  .attr("transform", "translate(100,350)");  
    
    legend2.append('text')
          .attr("x", (f,i)=>i*30+28)
          .attr("y", 84)
          .attr("id", "lines")
          .text("|");  
    
    legend2.append('text')
          .attr("x", (f,i)=>(i*30)+20)
          .attr("y", 100)
          .style("font-size",16)
          .text((f,i)=>f);   
    
    svg.append("g")
       .attr("transform","translate(" + 0 + "," + 377 + ")")
       .attr("id","x-axis")
       .call(xAxis);
    
    svg.append("g")
       .attr("transform","translate(" + 98 + "," + 15 + ")")
       .attr("id","y-axis")
       .call(yAxis);   

```

---

## Installation
## Features
## Usage (Optional)
## Documentation (Optional)
## Tests (Optional)
## Contributing

## Team

> Contributors/People

| [**seansangh**](https://github.com/seansangh) |
| :---: |
| [![seansangh](https://avatars0.githubusercontent.com/u/45724640?v=3&s=200)](https://github.com/seansangh)    |
| [`github.com/seansangh`](https://github.com/seansangh) | 

-  GitHub user profile

---

## FAQ

- **Have any *specific* questions?**
    - Use the information provided under *Support* for answers

---

## Support

Reach out to me at one of the following places!

- Twitter at [`@wwinvestingllc`](https://twitter.com/wwinvestingllc?lang=en)
- Github at [`seansangh`](https://github.com/seansangh)

---

## Donations (Optional)

- If you appreciate the code provided herein, feel free to donate to the author via [Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4VED5H2K8Z4TU&source=url).

[<img src="https://www.paypalobjects.com/webstatic/en_US/i/buttons/cc-badges-ppppcmcvdam.png" alt="Pay with PayPal, PayPal Credit or any major credit card" />](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4VED5H2K8Z4TU&source=url)

---

## License

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

- **[MIT license](http://opensource.org/licenses/mit-license.php)**
- Copyright 2019 © <a>S.S.</a>
