<script lang="ts">
  import type { Options } from 'highcharts';
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

  const pieOptions1: Options = {
    chart: { type: "pie", backgroundColor: "transparent" },
    title: { 
      text: "Black" ,
    style: {
                color: "#F0BF56",
                fontSize: "1.1em",
                fontFamily: "Courier New, Courier, monospace",
            }},
    series: [
      {
        name: "Percentage", 
      type: "pie", 
      data: [
        { name: "Recived", y: 10.2, 
          color: "#5EA5D8" 
        },
        { name: "Did Not Receive", y: 89.8,
          color: "#F28D5A"
         }
      ]
    }]
  };

  const pieOptions2: Options = {
    chart: { type: "pie", backgroundColor: "transparent" },
    title: { 
      text: "Hispanic",
      style: {
                color: "#F0BF56",
                fontSize: "1.1em",
                fontFamily: "Courier New, Courier, monospace",
            }

    },
    series: [
      {
      name: "Percentage", 
      type: "pie",
      data: [
        { name: "Recived", y: 8.0,
          color: "#5EA5D8" 
         },
        { name: "Did Not Receive", y: 92.0,
          color: "#F28D5A"
         }
      ]
    }]
  };

  const pieOptions3: Options = {
    chart: { type: "pie", backgroundColor: "transparent" },
    title: { 
      text: "White" ,
    style: {
                color: "#F0BF56",
                fontSize: "1.1em",
                fontFamily: "Courier New, Courier, monospace",
            }},
    series: [
      {
        name: "Percentage", 
      type: "pie",
      data: [
        { name: "Recived", y: 17.2,
          color: "#5EA5D8" 
         },
        { name: "Did Not Receive", y: 82.8,
          color: "#F28D5A"
         }
      ]
    }]
  };
</script>

<div>
  <Scroller layout="right">
    {#snippet sticky()}

      

      <div class="chart-row">
    <div class="chart"><Chart options={pieOptions1} highcharts={Highcharts} /></div>
    <div class="chart"><Chart options={pieOptions2} highcharts={Highcharts} /></div>
    <div class="chart"><Chart options={pieOptions3} highcharts={Highcharts} /></div>
  </div>
  <p class=title>
        Percent of 18-28 Years Olds who Received Help Paying Tuition
      </p>

    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        For those who do enroll, family support plays a <strong>crucial role</strong>. Yet <a href="https://blackwealthdata.org/explore/assets"> data </a> shows that Black and Hispanic students are significantly 
        <strong>less likely to receive financial</strong> help with tuition compared to their White peers.
      </ArticleText>
      <ArticleText>
        This <strong>limits</strong> their financial flexibility during and after college, moreover, causes them to heavily rely on student loans, which can lead to <strong>long-term debt</strong>.
      </ArticleText>
      <ArticleText> 
        The result is <strong>unequal starting points</strong>, even when degree attainment is the same.
      </ArticleText>
      
    {/snippet}
  </Scroller>
</div>

<style>
 .chart-row {
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  flex-wrap: nonwrap; /* or wrap if you want them to stack on smaller screens */
  gap: 0.3rem;
}

.chart {
  flex: 1 1 1;
  max-width: 230px;
}

.title
  {
    color: #F0BF56;
    font-size: 1.3em;
    font-family: "Courier New", Courier, monospace;
    text-align: center;
    margin: 3rem;
    font-weight: bold;
    text-decoration: underline;
    
    
    
  }


</style>
