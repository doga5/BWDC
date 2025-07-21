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
                [2007, 18603],
                [2010, 18028],
                [2013, 22911],
                [2016, 23557],
                [2019, 26662],
                [2022, 25000],
                
            ],
            color: "#F28D5A",
        },
        {
            name: "Hispanic",
            data: [
                [2007, 14310],
                [2010, 15024],
                [2013, 16547],
                [2016, 22201],
                [2019, 20402],
                [2022, 13000],
            ],
            color: "#4096fa",
        },
        {
            name: "Black",
            data: [
                [2007, 13165],
                [2010, 17755],
                [2013, 19092],
                [2016, 24667],
                [2019, 34776],
                [2022, 26000],
                
            ],
            color: "#5EA5D8",
        },
         {
            name: "Other",
            data: [
                [2007, 14310],
                [2010, 15024],
                [2013, 20365],
                [2016, 23434],
                [2019, 22025],
                [2022, 25000],
            ],
            color: "#994646",
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
            text: "Median Education Loans for Households",
            style: {
                color: "#F0BF56",
                fontSize: "1.7em",
                fontFamily: "Courier New, Courier, monospace",
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
        gridLineColor: "#8c2b5a",
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
            The <strong>education debt</strong> for students in the U.S. has been a <strong>continuing concern</strong>, 
            increasing steadily over the years.
        </ArticleText>

            <ArticleText>
                <strong>Black households</strong>, in particular, have historically carried the 
                <strong>highest median education debt</strong>, peaking around $35,000 in 2019, 
                significantly above the levels of other groups.
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
