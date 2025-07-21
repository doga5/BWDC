<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const series = [
        {
            name: "White",
            data: [
    
                [2010, 67380],
                [2013, 65000],
                [2016, 67760],
                [2019, 70660],
                [2022, 71650],
                
            ],
            color: "#F28D5A",
        },
        {
            name: "Hispanic",
            data: [
                [2010, 60220],
                [2013, 58780],
                [2016, 61530],
                [2019, 58320],
                [2022, 60200],
            ],
            color: "#994646",
        },
        {
            name: "Black",
            data: [
    
                [2010, 56120],
                [2013, 57420],
                [2016, 62000],
                [2019, 55060],
                [2022, 61150],
                
            ],
            color: "#5EA5D8",
        },
         {
            name: "Asian",
            data: [
        
                [2010, 80910],
                [2013, 77410],
                [2016, 85580],
                [2019, 85150],
                [2022, 91130],
            ],
            color: "#4096fa",
        },
    ];

    let chart;
    let thirdSeriesVisible = false;

    let options = {
        chart: {
            type: "spline",
            backgroundColor: "#540023",
            
            

        },
        title: {
            text: "Median Annnual Earnings for Full-Time Workers",
            style: {
                color: "#F0BF56",
                fontSize: "1.7em",
                fontFamily: "Courier New, Courier, monospace",
            },
        },
        subtitle: {
            text: "(25-34 years old, Bachelor's degree or higher)",
            style: {
                color: "#F0BF56",
                fontSize: "1.3em",
                fontFamily: "Courier New, Courier, monospace",
            },
        },
         xAxis: {
        lineColor: "#F0BF56",
        labels: {
            style: {
                color: "#F0BF56",
                fontFamily: "Courier New, Courier, monospace",
            }
        },
        title: {
            style: {
                color: "#F0BF56"
            }
        }
    },
    yAxis: {
        gridLineColor: "#24000f",
        lineColor: "#F0BF56",
        labels: {
            style: {
                color: "#F0BF56",
                fontFamily: "Courier New, Courier, monospace",
                
            }
        },
        title: {
            text: "U.S. Dolars",
            style: {
                color: "#F0BF56",
                fontFamily: "Courier New, Courier, monospace",
            }
        }
    },
    legend: {
    itemStyle: {
        color: "#F0BF56", 
        fontSize: "14px",
        fontFamily: "Courier New, Courier, monospace",
    }
},
        series: [series[0], series[1], series[2],series[3]],
    };

    function toggleThirdSeries() {
        const existingSeries = chart.series.find((s) => s.name === "Group 3");

        if (existingSeries) {
            existingSeries.remove();
            thirdSeriesVisible = false;
        } else {
            chart.addSeries(series[2]);
            thirdSeriesVisible = true;
        }
    }
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <div class="chart">
                <Chart bind:chart {options} highcharts={Highcharts} />
            </div>
           
            <div>
            
                <p class="chart-description"> 
                    Click the labels to see the data for a specific race/ethnicity.
    
                </p>
                <style >
                    .chart-description {
                        color: #f8edf2;
                        font-size: 1em;
                        margin-top: 1.5rem;
                        text-align: center;
                        font-family: "Courier New", Courier, monospace;
                        border: 1px dotted #F0BF56;
                        padding: 1rem;
                        border-radius: 15px;
                    }

                </style>
               
            </div>
        {/snippet}

        {#snippet scrolly()}
    

            <ArticleText>
                And yet, the <strong>benefits</strong> of a college education 
                are <strong>not equally distributed</strong> across different racial and ethnic groups. 
                
            </ArticleText>

            <ArticleText>
                The <a href="https://blackwealthdata.org/explore/employment#EMP-01">data</a> show that 
                <strong>median annual earnings vary significantly among newly graduated workers</strong>.
                Black workers earn roughly $61,000 per year, $10,000 less than White workers and $30,000 less than their Asian peers.
                
             </ArticleText>
             <ArticleText>
                Despite holding the <strong>same level of education</strong>, young Black workers consistently earn less than their White and Asian peers.
                These persistent wage gaps suggest that <strong>a college degree alone is not enough to close racial income disparities</strong>, 
                pointing to deeper inequalities in the labor market.
                
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
