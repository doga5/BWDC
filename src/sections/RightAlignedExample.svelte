<script>
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

  const options = {
        chart: {
            type: "column",
            backgroundColor: "#540023"
        },
        title: {
            text: "Undergradute Enrollment Rates",
            style: {
                color: "#F0BF56",
                fontSize: "1.7em",
                fontFamily: "Courier New, Courier, monospace",
            }
        },
        
        xAxis: {
            categories: ["Asian", "Black", "Hispanic", "White"],
            crosshair: true,
            labels: {
                style: {
                    color: "#F0BF56",
                    fontSize: "14px"
                }
            }
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
                text: null
            },
            labels: {
                format: "{value}%",
                style: {
                    color: "#F0BF56"
                }
            }
        },
        tooltip: {
            shared: true,
            valueSuffix: '%'
        },
        plotOptions: {
            column: {
                pointPadding: 0.2,
                borderWidth: 0
            }
        },
        series: [
            {
                name: "2016",
                data: [8.4, 7.7, 6.5, 5.7],
                color: "#F28D5A"
            },
            {
                name: "2023",
                data: [6.9, 6.1, 5.9, 4.8],
                color: "#4096fa"
            }
        ],
         legend: {
    itemStyle: {
        color: "#F0BF56", 
        fontSize: "14px",
        fontFamily: "Courier New, Courier, monospace",
    }
},
    };
</script>



<div>
  <Scroller layout="right">
    {#snippet sticky()}
      <div class="chart">
        <Chart {options} highcharts={Highcharts} />
      </div>
      
        
      <p>
        Use the
        <a href="https://api.highcharts.com/highcharts/">API reference</a>
        to understand what each element in the <code>options</code> object does.
      </p>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        <strong>Welcome to the KWK Data Scrollytelling Template!</strong>
      </ArticleText>

      <ArticleText>
        This is a <strong>basic example</strong> of how you might create a scrollytelling
        piece using Svelte and Highcharts.
      </ArticleText>

      <ArticleText>
        You can use this template as a <strong>starting point</strong>
        for your project.
        <br /><br />
        Or, if you want to build something from scratch, you can use it as a
        <strong>reference</strong> for specific functionality.
      </ArticleText>

      <ArticleText>
        This is <strong>just one way</strong> that scrollytelling can look.
        <br /><br />
        <strong>
          If you use this template, be sure to modify it and make it your own!
        </strong>
      </ArticleText>
    {/snippet}
  </Scroller>
</div>

<style>
  .chart {
    width: 100%;
    margin: 0px auto;
    
  }
</style>
