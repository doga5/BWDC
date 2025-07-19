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
                You might notice that this basic template doesn't have certain
                features that are common in scrollytelling.
            </ArticleText>

            <ArticleText>
                For example, you might want a component that doesn't feature a
                sticky component at all. Or a component that is solely a sticky
                component.
            </ArticleText>

            <ArticleText>
                You might also want to add more interactivity or gamify parts of
                your scrollytelling piece.
            </ArticleText>

            <ArticleText>
                <strong>
                    It's up to you to research how to create the effects and
                    functionality that you envision!
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
