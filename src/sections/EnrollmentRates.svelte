<script>
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

  const options = {
    chart: {
      type: "column",
      backgroundColor: "#540023",
    },
    title: {
      text: "Undergradute Enrollment Rates",
      style: {
        color: "#F0BF56",
        fontSize: "1.7em",
        fontFamily: "Courier New, Courier, monospace",
      },
    },

    xAxis: {
      categories: ["Asian", "Black", "Hispanic", "White"],
      crosshair: true,
      labels: {
        style: {
          color: "#F0BF56",
          fontSize: "14px",
        },
      },
    },

    subtitle: {
      text: "by Race/Ethnicity",
      style: {
        color: "#F0BF56",
        fontSize: "1.3em",
        fontFamily: "Courier New, Courier, monospace",
      },
    },

    yAxis: {
      min: 0,
      lineColor: "#F0BF56",
      title: {
        text: null,
      },
      labels: {
        format: "{value}%",
        style: {
          color: "#F0BF56",
        },
      },
    },
    tooltip: {
      shared: true,
      valueSuffix: "%",
    },
    plotOptions: {
      column: {
        pointPadding: 0.2,
        borderWidth: 0,
      },
    },
    series: [
      {
        name: "2016",
        data: [8.4, 7.7, 6.5, 5.7],
        color: "#F28D5A",
      },
      {
        name: "2023",
        data: [6.9, 6.1, 5.9, 4.8],
        color: "#4096fa",
      },
    ],
    legend: {
      itemStyle: {
        color: "#F0BF56",
        fontSize: "14px",
        fontFamily: "Courier New, Courier, monospace",
      },
    },
  };
</script>

<div>
  <Scroller layout="right">
    {#snippet sticky()}
      <div class="chart">
        <Chart {options} highcharts={Highcharts} />
      </div>

      
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
       Each year, <strong>millions of students </strong> enroll in colleges and universities across the <strong>United States</strong>,
        seeking to improve their lives and those of their families. Defying the odds, they work hard to earn a degree with the promises of <strong>a better job and a brighter future.</strong> 
                
      </ArticleText>

      <ArticleText>
       The data obtained from <a href="https://blackwealthdata.org/explore/education"> BWDC </a> indicates that the undergraduate enrollment rates for <strong>Asian</strong> and <strong>Black</strong> 
      students have been consistently <strong>higher</strong> than those for <strong>White</strong> and <strong>Hispanic</strong> students. 
      </ArticleText>


      <ArticleText>
        On the other hand, undergraduate enrollment is <strong>shrinking for all groups</strong>, which could reflect rising tuition costs, economic instability, 
        or <strong>growing doubts about whether a degree guarantees better income</strong>, especially for students of color.
                
      </ArticleText>

    

      
    {/snippet}
  </Scroller>
</div>

<style>
  .chart {
    width: 100%;
    margin: 0px auto;
  }


@media (max-width: 600px) {
  .chart {
    width: 100%;
    margin: 0px auto;
  }
}
</style>