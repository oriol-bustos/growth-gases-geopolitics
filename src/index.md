```html
<span id="top"></span>
<div style="display: flex; flex-direction: column; align-items: center; text-align: center; width: 100%;">
  <!---<h1 style="border-top: 4px solid black; border-bottom: 4px solid black; padding: 15px 20px; display: inline-block; font-size: 2.2em; font-weight: bold; letter-spacing: 1px;">--->
  <h1 style="padding: 15px 20px; display: inline-block; font-size: 2.2em; font-weight: bold; letter-spacing: 1px;">
    Growth, Gases & Geopolitics
  </h1>
  <p class="subtitle"><em>Oriol Bustos Martínez - February 2025</em></p>
</div>

```

```js
html`<div style="display: flex; justify-content: center; align-items: center;">
  ${gg}
</div>`

```

```html
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <p>This notebook explores the evolution of global CO2 emissions across different economic groups over the past century. Thanks to 
    <b>Our World in Data's</b> Greenhouse Gas Emissions [<a href="https://ourworldindata.org/co2-and-greenhouse-gas-emissions">Dataset</a>], 
    and using interactive visualizations, it highlights the shifting reliance on various energy sources among high- and low-income nations.</p>
    
  <p>The analysis examines the economic, geopolitical, and environmental causes and implications of the observed transitions, showing how energy dependencies interact with global power structures and policy decisions.</p>
  
</div>

<div style="display: flex; justify-content: center; width: 100%; margin-top: 0px;">
  <div style="display: flex; width: 50%; justify-content: center; flex-direction: column; align-items: center; text-align: center; padding: 5px; border: 2px solid #ddd; border-radius: 20px; background-color: #fef4e5; margin-top: 20px;">
    <p style="font-size: 1.1em; font-weight: 500; color: #333; margin-top: 20px; margin-bottom: 10px;">
      Can we save the world? 🌍
    </p>
    <p style="font-size: 0.9em; font-weight: 500; color: #333; margin-top: 0px;">
      Stay until the end to play around with an interactive simulation.
    </p>
  </div>
</div>
<br><br>

```

```html

<span id="toc"></span>
<nav class="toc">
  <h2>Table of Contents</h2>
  <ul>
    <li><strong>1. Economy and Emissions</strong>
      <ul>
        <li><a href="#" onclick="document.getElementById('evolution-co2-gdp').scrollIntoView({ behavior: 'smooth' }); return false;">
          1.1 Evolution of CO₂ Emissions / GDP Growth</a></li>
        <li><a href="#" onclick="document.getElementById('heatmap-co2-gdp').scrollIntoView({ behavior: 'smooth' }); return false;">
          1.2 Heatmap of CO₂ vs GDP</a></li>
        <li><a href="#" onclick="document.getElementById('co2-gdp-regression').scrollIntoView({ behavior: 'smooth' }); return false;">
          1.3 CO₂ Emissions vs GDP Regression</a></li>
        <li><a href="#" onclick="document.getElementById('proportion-co2-sources').scrollIntoView({ behavior: 'smooth' }); return false;">
          1.4 Proportion of Use of 3 Main CO₂ Emitting Sources</a></li>
        <li><a href="#" onclick="document.getElementById('distribution-co2-time').scrollIntoView({ behavior: 'smooth' }); return false;">
          1.5 Distribution of CO₂ Sources Over Time</a></li>
        <li><a href="#" onclick="document.getElementById('correlation-gdp-co2').scrollIntoView({ behavior: 'smooth' }); return false;">
          1.6 Correlation Between GDP and CO₂</a></li>
      </ul>
    </li>
    
    <li><strong>2. Politics and Pollution</strong>
      <ul>
        <li><a href="#" onclick="document.getElementById('global-view').scrollIntoView({ behavior: 'smooth' }); return false;">
          2.1 A Global Point of View</a></li>
        <li><a href="#" onclick="document.getElementById('co2-trading-lie').scrollIntoView({ behavior: 'smooth' }); return false;">
          2.2 CO₂ Trading, The Big Lie</a></li>
        <li><a href="#" onclick="document.getElementById('trump-is-back').scrollIntoView({ behavior: 'smooth' }); return false;">
          2.3 Trump is Back</a></li>
        <li><a href="#" onclick="document.getElementById('lets-step-back').scrollIntoView({ behavior: 'smooth' }); return false;">
          2.4 Let's Step Back</a></li>
        <li><a href="#" onclick="document.getElementById('global-temp-variations').scrollIntoView({ behavior: 'smooth' }); return false;">
          2.5 Global Temperature Variations Over History</a></li>
        <li><a href="#" onclick="document.getElementById('paris-agreement').scrollIntoView({ behavior: 'smooth' }); return false;">
          2.6 Are We Still on Time? The Paris Agreement</a></li>
      </ul>
    </li>
  </ul>
</nav>

```

```html
<div style="max-width: 800px; padding: 15px; border-left: 6px solid #444; background-color: #f8f8f8; text-align: left; margin-top: 20px;">
    <h4 style="margin-top: 0;">‼️Loading time ‼️</h4>
    <p>
      <em>
      Some plots are more data-heavy than others, while you scroll some may still be loading. Be patient, I tried to make the initial ones appear quickly, while others run. 
    </p>
  </div>
</div>

<br><br>
<br>


```

```html

<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h2 style="text-align: center; margin-bottom: 0px;">1 - Economy and Emissions</h2>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;margin-top: 0px">
    <p>The initial focus of the analysis will be put on the relationship between pollution and production, emissions and growth, CO2 and GDP. </p>
    <p>Are CO2 emissions a necessary or sufficient condition for economic development? We will start with a global view a progressively get into more details.</p>
  <p></p>
</div>
```

```html
<span id="evolution-co2-gdp"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">📈 1.1 - Evolution of CO2 Emissions / GDP Growth</h3>
  <p class="subtitle"><em>Do we need CO2 to grow? Worldview in relative terms.</em></p>


  <p>This map visually displays how <strong>CO₂ emissions per unit of GDP (kg/$)</strong> vary across different countries worldwide. The countries are colored based on the amount of CO₂ they generate relative to their economic output, enabling the identification of global emission patterns.</p>
  <p>Countries with <strong>industrial sectors</strong> often show <strong>higher values</strong> on this map. This is because industries typically produce significant CO₂ emissions, especially in economies reliant on manufacturing, heavy industry, or fossil fuels. In contrast, countries with more service-oriented economies or advanced technologies may exhibit <strong>lower CO₂ emissions per GDP unit</strong>, reflecting greater efficiency or cleaner energy sources.</p>

  <div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
    <div style="transform: scale(1); transform-origin: center; padding: 0px; margin-bottom: 20px;">${viewof selected_year_map_co2gdp}</div>
    <div style="transform: scale(0.9); transform-origin: center; padding: 0px; margin-top: -40px; margin-bottom: 15px;">${world_map_co2gdp_plot}</div>
      <div style="transform: scale(1); transform-origin: center; padding: 0px; margin-top: -150px; margin-bottom: 30px; font-size: 20px; font-weight: bold; color: #bababa">Year ${selected_year_map_co2gdp}: ${period}</div>
  </div>
<br><br>
<div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Here we have a world map using the "<code>equal-earth</code>" projection, which preserves the realtive sizes of countries and continents.<br> 
        - By default we would have the "<code>mercator</code>" projection, a conformal projection that preserves angles and shapes but distorts area.<br>
        - The year count on the bottom also displays the current era (defined arbitrarily).<br>
      </em>
    </p>
</div>
  <div style="max-width: 800px; padding: 15px; border-left: 6px solid #444; background-color: #f8f8f8; text-align: left; margin-top: 20px;">
    <h4 style="margin-top: 0;">📌 Economical Note: Inflation-adjusted GDP data</h4>
    <p>
  The analysis uses inflation-adjusted GDP data that accounts for changes in relative prices over time.
  As noted in Maddison’s methodology [<a href="https://onlinelibrary.wiley.com/doi/10.1111/joes.12618" target="_blank">Journal of Economic Surveys</a>], constant price extrapolation overlooks economic structural shifts. To enhance accuracy, we follow modern correction standards, refining historical GDP trends.
    </p>
  </div>


  <!-- Additional historical note about the UK -->
  <div style="max-width: 800px; padding: 15px; border-left: 6px solid #444; background-color: #f8f8f8; text-align: left; margin-top: 20px;">
    <h4 style="margin-top: 0;">📌 Historical Note: The UK and Its Global Reach</h4>
    <p>
      When analyzing this data, it is crucial to recognize that 
      for many years, the "United Kingdom" was not just Great Britain. During its peak, 
      the British Empire included vast territories across the world such as:
    </p>
    <ul>
      <li>Nort-America: Canada, the 13 Colonies...</li>
      <li>Australia and New Zealand</li>
      <li>India</li>
      <li>South Africa</li>
      <li>Parts of the Caribbean (e.g., Jamaica, Barbados)</li>
      <li>Large portions of Africa (e.g., Nigeria, Kenya, Egypt)</li>
      <li>Hong Kong, Malaysia, and other parts of Asia</li>
    </ul>
    <p>
      These regions played important roles in the economic output and industrial activities 
      attributed to the UK, affecting GDP and CO₂ emissions computations 
      They are however, missing in the map, as it only paints the current territory. UK is not the only country that shows this phenomena.
    </p>
  </div>
</div>

```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

---

```html
<span id="heatmap-co2-gdp"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">🟥🟨 1.2 - Same Message, Different Perspective🟨🟥</h3>
    <p class="subtitle"><em>Heatmap of the Relationship between CO2 Emissions and GDP by Year Interval and Country</em></p>
  <p>This heatmap illustrates the <b>average CO2 emissions per GDP (kg/$)</b> for selected countries across decades, highlighting how emissions evolve with economic development. Each cell's color reflects CO2 intensity, helping to identify patterns and trends over time.</p>
  
  <h3 style="text-align: center;">Patterns and Economic Development</h3>
  <ul style="text-align: left; max-width: 600px;">
    <li><b>Industrial Beginnings:</b> Nations in early industrial stages rely heavily on <b>fossil fuels like coal</b>, leading to high CO2 emissions per GDP. This is often reflected in darker-colored cells for earlier decades.</li>
    <li><b>Energy Transition:</b> As economies grow, they adopt <b>cleaner energy sources</b> such as renewables and nuclear, reducing emissions and improving efficiency.</li>
    <li><b>Optimized Advanced Economies:</b> Developed nations benefit from <b>energy-efficient technologies</b>, cleaner energy, and a shift toward <b>service-based industries</b>, leading to lower CO2 emissions per GDP.</li>
  </ul>
  
  <div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
    <div style="transform: scale(0.9); transform-origin: center; padding: 0px; margin-top: -40px; margin-bottom: 15px;">${heatmap}</div>
  </div>
</div>

<div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Here we have the same information displayed with a <strong>heatmap</strong>.<br> 
        - The color palette is consistent with the previous plot, with strong red meaning we have a less efficient economy in ecological terms.<br>
        - Countries have been ordered by geological proximity as accurately as possible, though some deviations remain unavoidable.<br>
      </em>
    </p>
</div>
```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

---

```html
<span id="co2-gdp-regression"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">📊 1.3 - CO2 Emissions vs. GDP per Capita</h3>
    <p class="subtitle"><em>A Comparative Analysis for the 10 richest and poorest countries</em></p>
  <p>This visualization demonstrates the relationship between CO2 emissions per capita and GDP per capita. Wealthier nations tend to produce higher emissions due to increased industrial activity and energy consumption. Conversely, poorer nations cluster in the lower-left quadrant, exhibiting both low GDP and emissions, often relying on low-carbon energy sources due to limited industrialization.</p>
  <p>The dashed blue regression line represents the global average relationship between CO₂ emissions per capita and GDP per capita. Its slope indicates the typical ratio of CO₂ emissions to economic output, showing how emissions tend to scale with wealth. The shaded region around the line represents the standard deviation, illustrating the uncertainty and variation in this relationship across different countries.</p>
  <p>Countries above the regression line are emitting more CO₂ than expected for their GDP, often due to energy-intensive industries or heavy reliance on fossil fuels. This includes nations like Saudi Arabia and the UAE, where economic wealth is closely tied to oil production. Conversely, countries below the regression line are emitting less CO₂ than expected for their GDP, often due to cleaner energy policies, efficient energy use, or a service-based economy. Nations such as Norway and Switzerland exemplify this trend, demonstrating that economic prosperity can be achieved with relatively lower emissions.</p>
  <p>This shows the broader challenge of decoupling economic growth from carbon emissions in the pursuit of sustainable development. Understanding these variations is crucial for designing targeted policies that promote cleaner energy transitions while supporting economic stability.</p>
  <div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
    <div style="transform: scale(1); transform-origin: center; padding: 0px; margin-bottom: 20px;">${viewof year_reg_plot}</div>
    <div style="transform: scale(0.9); transform-origin: center; padding: 0px; margin-top: -40px; margin-bottom: 15px;">${regression_plot3}</div>
  </div>

  <div style="max-width: 800px; padding: 15px; border-left: 6px solid #444; background-color: #f8f8f8; text-align: left; margin-top: 20px;">
    <h4 style="margin-top: 0;">‼️Loading time ‼️</h4>
    <p>
      <em>
      This plot takes quite a while to load all the data, so you may see empty years. Restart the play button or play around with the slider and after some tries it should load, if not wait some time while you continue. 
      </em>
    </p>
  </div>
</div>
<div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Here we we have a <strong>scatter plot</strong>, with a regression line and its standard deviation range around it.<br>
        - I am only representing the top 10 richest, and top 10 poorest countries to avoid clutter.<br>
        - The x-axis is in <strong>logarithmic scale</strong>, but not the y-axis.<br>
        - The size of the dots represents their population.<br>
        - The color palette for continents will remain consistent across the remaining notebook.<br>
      </em>
    </p>
</div>
```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

---

```html
<span id="proportion-co2-sources"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 10px;"> 🛢️⛽ 🏭</h3>
  <h3 style="text-align: center; margin-bottom: 10px;">  1.4 - Proportion of Use of the 3 Main CO2-Emitting Sources</h3>
  <p class="subtitle"><em> Grouped By Rich and Poor Countries</em></p>
  <p>This chart illustrates the contrasting energy reliance between economic groups over time. In the early 20th century, wealthier countries were heavily dependent on coal, accounting for over 90% of their CO2 emissions. However, as these economies developed and outsourced manufacturing, their energy mix became more balanced, with increased reliance on oil and gas and a notable decline in coal usage.</p>

  <p>In contrast, poorer countries historically relied more on oil. Over time, they followed a pattern similar to that of wealthier nations during the early 1900s, increasing their coal consumption. More recently, these nations have shifted back to oil-dominated CO2 emissions.</p>

  <p>This pattern highlights the persistent challenge less developed nations face in transitioning to cleaner energy sources while addressing their economic and developmental needs.</p>

  <div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
    <div style="transform: scale(1); transform-origin: center; padding: 0px; margin-bottom: 20px;">${viewof yearRadar}</div>
    <div style="transform: scale(0.9); transform-origin: center; padding: 0px; margin-top: -40px; margin-bottom: 15px;">${radar_plot}</div>
      <div style="transform: scale(1); transform-origin: center; padding: 0px; margin-left: 50px;margin-top: -120px; margin-bottom: 30px; font-size: 20px; font-weight: bold; color: #bababa">Year ${yearRadar}</div>
  </div>
</div>

<div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Here we have a <strong>radar plot</strong>.<br>
        - Represents parts of a total, in this case the total CO2 emitted by these 3 sources per group.<br>
        - A more balanced radar plot signifies more diversified energy sources, but not necessarily less consumption of any of the three materials.<br>
      </em>
    </p>
</div>
```

---

```html
<span id="distribution-co2-time"></span>
<div style="display: flex; width: 100%; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">⚖️ 1.5 - Distribution of CO2 Sources Over Time</h3>
  <p>After some birds-eye view, here we can see a more fine-grained picture. This next visualization allows inspecting the distribution of all CO2 emitting sources for each country over time. Moreover, a certain period can be selected by moving the cut-off year bars. It is difficult to make a commentary on a general note, as each country experienced a different path. What is clear is that all countries show a very sharp increase in overall CO2 emissions.</p>
  
  <p>It can be seen, for example, how Europe depended extremely heavily on coal (see the very beginning of Germany's stacked plot). After WWII, coal use did not really decrease, as we may think exploring the radar plot, but rather other sources started to pick up the pace. It's only in the late 20th century when coal started to reduce in absolute terms.</p>

  <div style="padding: 0px; margin-bottom: 20px;">${viewof selected_country_energy_sources}</div>
  <div style="padding: 0px; margin-bottom: 20px;">${viewof selected_window_year_energy_sources}</div>
  <div style="padding: 0px; margin-bottom: 20px;">${viewof selected_year_energy_sources}</div>
  

  <!-- FLEX CONTAINER FOR BOTH PLOTS -->
  <div style="display: flex; width: 100%; justify-content: space-between; margin-top: 20px;">

    <!-- Stacked Plot -->
    <div style="width: 62%; transform: scale(0.9); transform-origin: center; padding: 0px;">
      ${stacked_plot}
    </div>

    <div style="width: 38%; transform: scale(1); transform-origin: center; padding: 0px;">
      ${treemap_chart}
    </div>

  </div>

</div>
<div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - On the left we have a <strong>stacked plot</strong>, on the right a <strong>treemap chart</strong>.<br>
        - THe color palette is consistent between both plots.<br>
        - The vertical line in the stacked plot corresponds to the cutting year in the treemap.<br>
      </em>
    </p>
</div>

<div style="max-width: 500px; padding: 15px; border-left: 6px solid #007bff; border-right: 6px solid #007bff; background-color: #eef5ff; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #0056b3;font-family: 'Helvetica';">⚙️ Plot Settings</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - First, select a country to visualize.<br>
        - Secondly, choose a year range to visualize the cumulative CO2 stacked plot.<br>
        - Finally select a cut year to inspect in more detail the distribution of CO2-emitting sources, notice it corresponds to the vertical line in the stacked plot.<br>
        - Hovering over elements may reveal precise values and insights.<br>
    </p>
</div>

```

---

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

```html
<span id="correlation-gdp-co2"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">🔗 1.6 - Correlation Between GDP and CO2 by Half-Century and Country Group</h3>
  <p>Finally, taking a step back again, we again look into the relationship between growth and contamination from a different perspective. In this plot, the x-axis represents the correlation coefficient between GDP per capita and CO2, <b>radius of the dots represents the economy size</b>. </p>

  <p>Observing the plot, it is apparent that countries exhibiting high growth rates typically have higher positive correlation values between GDP per capita and CO2 emissions. This suggests that, historically, economic expansion has often gone hand-in-hand with increased carbon emissions. However, the pattern shift when economies grow. In modern nations, economic growth has begun to decouple from CO2 emissions, as evidenced by dots slowly gravitating toward the center, thus lower correlation values.</p>

<p>This shift implies that some economies are making progress towards sustainable growth, potentially driven by improved efficiency, the use of renewable sources, technological advancements, or effective environmental policies.

  <div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
    <div style="transform: scale(0.9); transform-origin: center; padding: 0px; margin-top: -40px; margin-bottom: 0px;">${corrPlot}</div>
  </div>
</div>

<div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Here we have a <strong>faceted scatter plot</strong>.<br> 
        - In each facet, there 8 groups of countries in the y axis. The x-axis represents the Pearson correlation coefficient between GDP and CO" for that group.<br>
        - Dot size represents economy size in absolute terms (GDP).<br>
        - Color represents mean annualized economy growth.<br>
      </em>
    </p>
</div>
```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 1.2em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

---

```html

<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h2 style="text-align: center; margin-bottom: 0px;">2 - Politics and Pollution</h2>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;margin-top: 0px">
    <p>In this second part we will explore emissions in more absolute terms, not so much in relation to economic output, explore the effects of policy changes, see who really matters in this discussion, and what are our chances for keeping global warming in line </p>
  <p></p>
</div>
```

```html
<span id="global-view"></span>
<div>
  <div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">🌐 2.1 - A Global Point of View 🌐</h3>
  <p class="subtitle"><em>Starting off with a birds-eye over where all those CO2 emissions are coming from, in absolute terms, across time.</em></p>

  <div style="transform: scale(1); transform-origin: center; padding: 0px; margin-bottom: 20px;">${viewof selected_year_triple_map}</div>
  <div class="box">
    <div width = 80%>${viewof triple_world_map}</div>
    <div width = 20%>${chart2}</div>
    <div width = 100%>${chart3}</div>
  </div>
</div>`
<div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Here we have a three charts, including a worldmap, a time series and an horizontal barplot.<br> 
        - Dot sizes in the map represent CO2 emissions.
        - In the bottom plot a race in typical Instagram Reels fashion shows the leaderboard for the most polluting countries in the world.<br>
        - By default we would have the "<code>mercator</code>" projection, a conformal projection that preserves angles and shapes but distorts area.<br>
      </em>
    </p>
</div>
<div style="max-width: 500px; padding: 15px; border-left: 6px solid #007bff; border-right: 6px solid #007bff; background-color: #eef5ff; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #0056b3;">⚙️ Plot Settings</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Click play and see the dots in the map grow as emissions increase.<br>
        - When the slider is stopped, hover over a specific country and notice the right plot showing its specific CO2 emissions time-series.<br>
    </p>
</div>
```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

---

```html
<span id="co2-trading-lie"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">🤥 2.2 - CO2 Trading, The Big Lie</h3>
  <p>If we hover some European or North American countries in the first visualization, in the previous plot we can see the time-series evolution of their emissions has dropped these last few years. Great! The developed countries are saving the world. Or are they? Are we sure the entirety of this drop is because they've become more efficient? Or because someone else (China and India) is doing the dirty job for them (USA, UK, Germany, etc.)?</p>
  <p>The top-left plot shows the CO2 emissions on the y-axis, and most importantly, the traded CO2 on the x-axis. COuntries that import goods that generate a lot of pollution during their production in the manufactaring country, move to the right, while does that actually produce the items, move to the left.</p>
  <p>We can see on the top-right plot that, yes, North-America and Europe have both stopped the exponential increase in emissions, even started to go down. But this has been at the expense of outsourcing the manufacturing, resulting in a global picture that jsut keeps climbing up. China is not entirely blameless, as exports are not the sole driver of its emissions. However, the key takeaway is that, despite apparent regional slowdowns, some may portrait themselves as heroes, blaming others while hiding the true reality of the situation. All of this while the global emissions continue to rise at an alarming rate.</p>

  <div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  
  <div style="transform: scale(1); transform-origin: center; padding: 0px; margin-bottom: 20px;">
    ${viewof selected_year_trading}
  </div>

  <!-- First Row: Two Side-by-Side Plots -->
  <div style="display: flex; width: 100%; justify-content: space-between; margin-top: 20px;">
    
    <!-- Stacked Plot -->
    <div style="width: 50%; transform: scale(0.9); transform-origin: center; padding: 0px;">
      ${trading_plot}
    </div>

    <!-- Second Plot -->
    <div style="width: 50%; transform: scale(1); transform-origin: center; padding: 0px;">
      ${primerplot}
    </div>

  </div> <!-- Close first row div -->

  <h3 style="text-align: center; margin-bottom: 0px;">Total Global Emissions</h3>
  <!-- Second Row: Third Plot Centered Below -->
  <div style="width: 100%; margin-top: 20px; display: flex; justify-content: center;">
    <div style="width: 80%; transform: scale(1); margin-top:-25px; transform-origin: center; padding: 0px;">
      ${segonplot}
    </div>
  </div>
  <div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - The top-left plot represents, most importantly, traded CO2 (by import or export of the goods produced while emitting that CO2), and CO2 per capita emissions in the y-axis. The dot size represents the population.<br> 
        - Both top plots have consistent palettes for continent filler colours.<br> 
        - All three plots have tooltip options, the first one showing the country name, while the other two have a following dashed vertical line that displays details about that year's CO2 emissions.<br>
      </em>
    </p>
</div>
</div>

```

```html
<br><br>

```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

---

```html
<span id="trump-is-back"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">2.3 - Trump is BACK❗</h3>
    <p class="subtitle"><em>U.S. Withdraws from Paris Agreement Again: What Could It Mean for CO₂ Emissions?</em></p>
  <p>On January 20, 2025, the President of the United States announced the country's withdrawal from the Paris Agreement, marking a significant shift in environmental policy. This decision follows a history of back-and-forth commitments: the U.S. joined the agreement in 2016, withdrew in 2020, and re-entered in 2021. Now, with another exit, questions arise about the potential consequences for carbon emissions and energy consumption in the country.</p>
  <p>The graph below illustrates the annual trend of total CO₂ emissions and primary energy consumption in the U.S. over recent years. Each vertex represents a certain year. A rightward movement in the trend indicates an increase in energy consumption, often linked to economic productivity. A downward movement suggests a reduction in CO₂ emissions. We can see the effect of the pandemic in the transition from 2019 to 2020. Historical shifts in U.S. climate policy have influenced these patterns, making it critical to examine how this latest withdrawal might impact the nation’s emissions trajectory. Will history repeat itself, leading to higher emissions, or will other factors counterbalance the decision?</p>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <div style="transform: scale(0.9); transform-origin: center; padding: 0px; margin-top: -40px; margin-bottom: 0px;">${trump}</div>
</div>

  <div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Here the x-axis represents energy consumption, a measure of economic activity and development.<br> 
        - The y-axis represents CO2 emissions.<br>
        - A drop in both axis results in a diagonal like the seen during the pandemic.<br>
        - The ideal shape to follow would be a downward diagonal to the right, where economy develops while emissions decrease.<br>
      </em>
    </p>
</div>
```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

---

```html
<span id="lets-step-back"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">🔙 2.4 - Let's step back</h3>
    <p class="subtitle"><em>What does the world say?</em></p>
  <p>The previous plot focused on the U.S. trajectory, but stepping back to a global scale reveals broader trends. While the U.S. has fluctuated in its emissions and energy consumption, China’s emissions have continued rising sharply, thrusting like a rocket, driven by its growing energy demand. In contrast, the European Union has lately been decreasing both its energy consumption and emissions, the only one from the group with a clear receding trend. </p>
  <p>India and Russia follow distinct paths—India’s emissions are rising alongside energy use, reflecting industrial growth, while Russia remains relatively stable. Will policies align to curb this trend, or will energy demand keep driving emissions upward?
</p>

    <div style="transform: scale(0.85); transform-origin: center; padding: 0px; margin-top: 0px; margin-bottom: -50px;">${rest_of_the_world}</div>
  <div>${viewof selected_rocket_year}</div>

    <div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Same idea as in the previous plot, but with a broader perspective, China shoots up like a rocket in an upward right diagonal.<br> 
        - If the selected interval is too big, the initial dots may grow a lot.<br> 
        -  Europe recedes in both terms, but the US is apparently able to withold energy consumption or even increse it a bit while reducing their emissions.<br>
      </em>
    </p>
</div>
  <div style="max-width: 500px; padding: 15px; border-left: 6px solid #007bff; border-right: 6px solid #007bff; background-color: #eef5ff; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #0056b3;">⚙️ Plot Settings</h4>
    <p style="color: #333;">
       <em>Change the interval years with the slider in the bottom:<br>
      <br>
  - You can extend on either side up until a maximum value <br>
  - OR move the interval (of 13 years by default), by dragging it from the middle part.<br>
  - Hover over each dot to see the year it corresponds to.<br>
    </p>
</div>
  

```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

---

```html
<span id="global-temp-variations"></span>
<div style="margin-top: 60px; display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">🌡️ 2.5 - Global Temperature Variations Over History</h3>
    <p class="subtitle"><em>Natural or man-made?</em></p>
  <p>This plot displays global temperature anomalies over the past 2000 years extracted from [<a href="https://www.technologyreview.com/2024/05/16/1092507/tree-rings-climate-data/">MIT's Technology Review</a>]. In this case an anomaly is defined as the deviation relative to the 20th-century average. For the majority of recorded history, temperatures remained predominantly below this baseline, as indicated by the blue shading. Only some sporadic years around the year 1000 A.D. were hotter than the baseline.</p>
    
   <p style="margin-bottom: 35px;"> However, in recent centuries—particularly after the Industrial Revolution—there has been a sharp and unprecedented rise in temperature anomalies, shown in red. This steep increase in global temperatures suggests a significant shift from natural variability to human-driven climate change, emphasizing the urgency of addressing global warming.</p>
  <div style="transform: scale(0.9); transform-origin: center; padding: 0px; margin-top: -40px; margin-bottom: 15px;">${temperature_over_time}</div>

    <div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - The timeline progresses at different intervals depending on the era: larger steps in early years and finer granularity in more recent years.<br>
        - The y-axis represents the difference between that specific's year temperature and the baseline (20th century mean).<br> 
      </em>
    </p>
</div>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
<div style="max-width: 800px; padding: 15px; border-left: 6px solid #007bff; border-right: 6px solid #007bff; background-color: #eef5ff; text-align: center; margin-top: 20px; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #0056b3;">⚙️ Plot Settings</h4>
    <p style="color: #333;">
        - <em>Use the <strong>"Resume"</strong> button to start or continue the animation, and the <strong>"Stop"</strong> button to pause it.<br>
        - Adjust the <strong>speed slider</strong> to control how fast the data progresses over time.<br>
        - The plot updates dynamically, revealing temperature changes over time. If you reach the last year, press <strong>"Resume"</strong> to restart from the beginning.<br>
    </p>
</div>
</div>
</div>

```

---

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('toc').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 0.8em; color: #007acc; text-decoration: none;">
      Back to Table of Contents
    </a>
  </p>
</div>

```

```html
<span id="paris-agreement"></span>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h3 style="text-align: center; margin-bottom: 0px;">⏳ 2.6 - Are We Still on Time?: The Paris Agreement </h3>
  <p class="subtitle"><em> Simulating the Effect of Annualized % Change in CO₂ Emissions Per Country Until 2030</em></p>

  <p>On the brink of a year when nations must strengthen their climate commitments under the Paris Agreement, a new report from the United Nations Environment Programme (UNEP) warns that unless global greenhouse gas emissions decrease by 7.6% annually from 2020 to 2030, the world will miss the chance to stay on track toward the goal of limiting temperature rise to 1.5°C, as outlined in the Paris Agreement.</p>
  <p>Despite Europe’s commitment to cutting emissions at a steady pace, this chart highlights that the overall trajectory depends on the collective action of all major emitters—particularly China, the United States, and the rest of the world as a whole. While Europe’s push is certainly a step in the right direction, the global scale of emissions means that its efforts alone cannot secure the 1.5°C target. China, for instance, remains a key player due to its vast economic growth and large share of global emissions, and the same applies to other populous nations whose energy demands are rising. The data underscores how essential it is for these large contributors to adopt ambitious policies, invest in cleaner technologies, and collaborate internationally. Ultimately, only a coordinated worldwide approach can keep the planet on track to meet the goals of the Paris Agreement.</p>

    <div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
    <div style="transform: scale(1); transform-origin: center; padding: 0px; margin-bottom: 20px;">${viewof form_variations}</div>
  </div>
</div>
```

```html
  <div style="display: flex; align-items: center; justify-content: flex-start; width: 100%;">
    <div style="flex-shrink: 0; transform: scale(0.8); margin-left: -100px;">${simulation}</div>
    <div style="transform: scale(0.7); margin-left: -250px;">${thermometer}</div>
  </div>

  <div style="max-width: 500px; padding: 15px; border-left: 6px solid #ff7f00; border-right: 6px solid #ff7f00; background-color: #fff4e6; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #cc6600;font-family: 'Helvetica';"">📊 Visual Strategy</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - The <strong>dashed red line</strong> represents the predicted annual GHG emissions based on the input sliders.<br>
        - The prediction is done up to 2030.<br> 
        - The vertical fixed line represents the year the agreement was signed (2019), we were on path to following initially due to Covid, but we quickly stepped out of it.<br>
        - The vertical coloured thick bars represent each country's contribution to the total GHG emissions, this is what you can modify.<br>
        - GHG increase global temperatures, that's why for each resulting total gases in 2030, we will be in a certain range of temperature increase (diffused coloured areas).<br>
        - The thermometer on the right is static and represents the already present consequences of GHG, the cumulative temperature increse up until 2023.<br>
      </em>
    </p>
</div>
<div style="max-width: 500px; padding: 15px; border-left: 6px solid #007bff; border-right: 6px solid #007bff; background-color: #eef5ff; text-align: center; margin: 20px auto; border-radius: 8px; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);">
    <h4 style="margin-top: 0; color: #0056b3;">⚙️ Plot Settings</h4>
    <p style="color: #333; text-align: center;">
      <em>
        - Move the sliders of each country to simulate the effect of increasing or decreasing a certain country's gas emissions in percentage (%) terms.<br>
        - Hover over the plot before the agreement year which will show a detailed tooltip with the exact quantity of GH emissions for that year.<br>
    </p>
</div>



```

```html

<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;">
  <h2 style="text-align: center; margin-bottom: 0px;">3 - Closing</h2>
<div style="display: flex; width: 100%; justify-content: center; flex-direction: column; align-items: center; text-align: center;margin-top: 0px">
    <p>After exploring the data and visualizations in this notebook, it’s clear that the relationship between economic growth, emissions, and geopolitics is deeply intertwined. </p>
      
      <p>Over the past century, wealthier nations have driven global energy consumption, often at the expense of environmental sustainability, while lower-income countries struggle to balance development with cleaner energy transitions. The changes in energy reliance (whether from fossil fuels to renewables or from one dominant energy player to another) have shaped global power structures, influencing policy decisions and international relations.</p>
        
  <p>Ultimately, the challenge isn’t just about reducing CO₂ emissions; it’s about addressing the economic and political systems that keep us locked into these patterns. The data suggests that without decisive action and global cooperation, the road to sustainability will remain an uphill battle.</p>
  <p></p>
</div>
```

```html
<div style="display: flex; justify-content: flex-end; padding-right: 10px;">
  <p>
    <a href="#" onclick="document.getElementById('top').scrollIntoView({ behavior: 'smooth' }); return false;" 
       style="font-weight: bold; font-size: 1.2em; color: #007acc; text-decoration: none;">
      Back to the top
    </a>
  </p>
</div>

```

```html
<div style="border-top: 3px solid black; margin-top: 30px; padding-top: 15px; text-align: right; font-size: 1em; font-weight: 600; color: #444;">
    O.B.
</div>
<br><br>
<br><br>
<br><br>

```

## Addendum

### Data

```table

```

### Imports

```js
import { toc } from "https://api.observablehq.com/@nebrius/indented-toc.js?v=3";
import { interval } from "https://api.observablehq.com/@mootari/range-slider.js?v=3";
```

```js
function Scrubber(values, {
  format = value => value,
  initial = 0,
  delay = null,
  autoplay = true,
  loop = true,
  loopDelay = null,
  alternate = false
} = {}) {
  values = Array.from(values);
  const form = html`<form style="font: 12px var(--sans-serif); font-variant-numeric: tabular-nums; display: flex; height: 33px; align-items: center;">
  <button name=b type=button style="margin-right: 0.4em; width: 5em;"></button>
  <label style="display: flex; align-items: center;">
    <input name=i type=range min=0 max=${values.length - 1} value=${initial} step=1 style="width: 180px;">
    <output name=o style="margin-left: 0.4em;"></output>
  </label>
</form>`;
  let frame = null;
  let timer = null;
  let interval = null;
  let direction = 1;
  function start() {
    form.b.textContent = "Pause";
    if (delay === null) frame = requestAnimationFrame(tick);
    else interval = setInterval(tick, delay);
  }
  function stop() {
    form.b.textContent = "Play";
    if (frame !== null) cancelAnimationFrame(frame), frame = null;
    if (timer !== null) clearTimeout(timer), timer = null;
    if (interval !== null) clearInterval(interval), interval = null;
  }
  function running() {
    return frame !== null || timer !== null || interval !== null;
  }
  function tick() {
    if (form.i.valueAsNumber === (direction > 0 ? values.length - 1 : direction < 0 ? 0 : NaN)) {
      if (!loop) return stop();
      if (alternate) direction = -direction;
      if (loopDelay !== null) {
        if (frame !== null) cancelAnimationFrame(frame), frame = null;
        if (interval !== null) clearInterval(interval), interval = null;
        timer = setTimeout(() => (step(), start()), loopDelay);
        return;
      }
    }
    if (delay === null) frame = requestAnimationFrame(tick);
    step();
  }
  function step() {
    form.i.valueAsNumber = (form.i.valueAsNumber + direction + values.length) % values.length;
    form.i.dispatchEvent(new CustomEvent("input", {bubbles: true}));
  }
  form.i.oninput = event => {
    if (event && event.isTrusted && running()) stop();
    form.value = values[form.i.valueAsNumber];
    form.o.value = format(form.value, form.i.valueAsNumber, values);
  };
  form.b.onclick = () => {
    if (running()) return stop();
    direction = alternate && form.i.valueAsNumber === values.length - 1 ? -1 : 1;
    form.i.valueAsNumber = (form.i.valueAsNumber + direction) % values.length;
    form.i.dispatchEvent(new CustomEvent("input", {bubbles: true}));
    start();
  };
  form.i.oninput();
  if (autoplay) start();
  else stop();
  Inputs.disposal(form).then(stop);
  return form;
}
```

### Preprocessing

```js
import { gg, cleanCorr, colorScaleHeatmap,filteredDataForHeatmap, selectedCountriesHeatmap, trump } from "https://api.observablehq.com/@oriol-bustos/ggg_processing.js";

```

#### Heatmap

```js
const heatmap = Plot.plot({
  width,
  height: 610,
  x: {
    label: "Years (Grouped by 5 years)",
    type: "band",
    domain: Array.from(
      new Set(filteredDataForHeatmap.map(d => d.decade))
    ).sort((a, b) => a - b), // Ordenar las décadas
  },
  y: {
    label: "Countries",
    domain: selectedCountriesHeatmap, // Mantener orden de los países seleccionados
  },
  color: {
    type: "threshold", // Escala con intervalos definidos
    domain: [0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.2, 1.4], // Intervalos de 0.2
    range: [0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.2, 1.4].map(colorScaleHeatmap), // Colores calculados desde `colorScale`
    label: "Average CO2 per GDP (kg/$)",
    legend: true, // Mostrar leyenda
  },
  marks: [
    Plot.cell(filteredDataForHeatmap, {
      x: "decade",
      y: "iso_code",
      fill: d =>
        d.avgCo2PerGdp !== null && d.avgCo2PerGdp !== undefined
          ? d.avgCo2PerGdp // Usar el valor si existe
          : "#cccccc", // Color gris para datos faltantes
      title: d =>
        `Country: ${d.iso_code}\nYears: ${d.decade}\nAverage CO2 per GDP: ${
          d.avgCo2PerGdp !== null ? d.avgCo2PerGdp.toFixed(2) : "No Data"
        }`,
    }),
  ],
  style: {
    background: "white",
    legend: {
      textAlign: "center",
    },
  },
});
```

#### Corrplot

```js
const corrPlot = Plot.plot({
  width,
  height: 800,
  marginBottom:50,
  marginRight: 70, // Increased margin for the legend
  marginLeft: 110,
  grid: "both", // Add finer gridlines
  x: {
    nice: true,
    label: "Correlation between per-capita GDP and CO₂",
    tickSize: 10,
    domain: [-1, 1], // Set the x-axis range explicitly
  },
  y: {
    inset: 5,
    label: "Country",
  },
  r:{range:[1.5,20]},
  fy: {
    label: "Half-Century", // Facet Y-axis label
    sort: { order: "ascending" }, // Sort facets in chronological order
    tickSize: 5},
  color: {
    legend: true,
    label: "Growth (% per year)", // Add a label to the legend
    type: "sequential",
    domain:[0,7],
    n: 4,
    scheme: "BuYlRd"
  },
  marks: [
    Plot.frame(),
    Plot.dot(cleanCorr, {
      x: "correlation",
      y: "group",
      fy: "halfCentury",
      r: d=> Math.pow(d.economySize, 1 / 1),
      fill: "growth",
      stroke: "black",
      strokeWidth: 0.7,
      //tip: true,
      title: d =>
        `${d.group}, ${d.halfCentury}\nCorrelation (GDP~CO2): ${d.correlation.toFixed(
          2
        )}\nAnnualized Growth: ${d.growth?.toFixed(2)}%\nEconomy Size: $${d.economySize?.toFixed(2)}`,
      sort: { y: "-x", fy: "y" } // Sort countries by correlation within each half-century
    }),
  ],
});

```

#### Map CO2 / GDP

```js
import {colorScale, countries_worldmap, countriesData} from "https://api.observablehq.com/@oriol-bustos/ggg_processing.js"
```

```js
viewof selected_year_map_co2gdp = Scrubber(d3.range(1850, 2023), {loop: false, delay: 25})
```

```js
const filteredData = owidCo2Data.filter(d => d.year === selected_year_map_co2gdp).map(d => ({gdpxgv: +d.gdp, co2xgv:+d.co2, ...d}))
```

```js
const dataByIso = new Map(
  filteredData.map(d => [
    d.iso_code,
    (d.co2 !== "" && d.gdp !== "" && +d.gdp !== 0) 
      ? ((+d.co2*1000000000)/+d.gdp)  
      : null 
  ])
)

// co2 is in millions of tons to convert it to kg we have to multiply per 1 billion (english unit)
// gdp is in dollars
```

```js
const world_map_co2gdp_plot = Plot.plot({
  width,
  height: 610,
  projection: "equal-earth",
  color: {
    type: "threshold", // Escala con umbrales
    domain: [0, 0.1, 0.2, 0.5, 1], // Puntos de los intervalos
    range: ["#f7f7f7", "#fee5d9", "#fcae91", "#fb6a4a", "#de2d26"], // Colores asociados
    label: "CO2 per GDP (kg/$)", // Etiqueta de la escala
    legend: true, // Mostrar la leyenda
    legendOptions: {
      ticks: [0, 0.1, 0.2, 0.5, 1], // Ticks específicos
      tickFormat: ",.1f kg/$", // Formato con unidades
      style: {
        fontSize: "12px", // Tamaño del texto
        fontFamily: "Arial, sans-serif", // Fuente del texto
      },
    },
  },
  marks: [
    Plot.geo(countries_worldmap, {
      fill: d => {
        const countryData = countriesData.find(data => data.iso_n3 === d.id); // Relación por `iso_n3`
        const iso = countryData?.adm0_a3_us; 
        const co2PerGdp = dataByIso.get(iso);

        if (co2PerGdp === null || co2PerGdp === undefined) {
          return "#f0f0f0"; // Color para datos ausentes
        }

        return colorScale(co2PerGdp); // Escala para valores existentes
      },
      stroke: "white", // Borde de los países
      title: d => {
        const countryData = countriesData.find(data => data.iso_n3 === d.id);
        const iso = countryData?.adm0_a3_us;
        const co2PerGdp = dataByIso.get(iso);

        if (co2PerGdp === null || co2PerGdp === undefined) {
          return `${countryData?.sovereignt || "Unknown Country"}\nNo Data`;
        }

        return `${countryData?.sovereignt || "Unknown Country"}\nCO2 per GDP: ${
          co2PerGdp.toFixed(2)
        } kg/$`;
      }
    }),
    
    Plot.geo(countries_worldmap, {stroke: "white", fill: "none"})
  ],
  style: {
    background: "white", // Fondo blanco
    legend: {
      marginTop: "10px", // Espacio entre leyenda y mapa
      textAlign: "center",
    }
  },

});
```

```js
function getPeriodName(year) {
  if (year < 1850 || year > 2024) {
    return "Out of range";
  } else if (year < 1900) {
    return "Early Industrialization";
  } else if (year < 1914) {
    return "Pre-World War I";
  } else if (year < 1919) {
    return "World War I";
  } else if (year < 1939) {
    return "Interwar Period";
  } else if (year < 1946) {
    return "World War II";
  } else if (year < 1973) {
    return "Post-War Economic Boom";
  } else if (year < 1990) {
    return "Energy Crisis & Global Shifts";
  } else if (year < 2010) {
    return "Globalization Era";
  } else {
    return "Contemporary Era";
  }
}

```

```js
period = getPeriodName(selected_year_map_co2gdp)
```

#### Simulations

#### Rocket Plot

```js
viewof selected_rocket_year = interval([1965, 2023], {
  step: 1,
  value: [2010, 2023],
  label: 'Select an Interval to Show',
})
```

```js
const rocket_year1 = selected_rocket_year[0]
```

```js
const rocket_year2 = selected_rocket_year[1]
```

```js
except_rest_world2 = Array.from(d3.rollup(
  co2_country_data.filter(row => row.year >= rocket_year1 && row.year <= rocket_year2),
  v => ({
    primary_energy_consumption: d3.sum(v, d => d.primary_energy_consumption),
    co2: d3.sum(v, d => d.co2)
  }),
  d => country_name_interested(d),
  d => d.year
)).flatMap(row => 
  Array.from(row[1]).map(kv => ({
    country_name: row[0], 
    year: Number(kv[0]), 
    primary_energy_consumption: kv[1].primary_energy_consumption, 
    co2: kv[1].co2
  }))
).filter(row => row.country_name != "Rest of World");

```

```js
last_flags_except_world2 = except_rest_world2.filter(row => row.year == rocket_year2).map(row => {
  if(row.country_name == "United States") {
    return Object({co2: row.co2, primary_energy_consumption: row.primary_energy_consumption,
                   flag: "https://upload.wikimedia.org/wikipedia/en/thumb/a/a4/Flag_of_the_United_States.svg/320px-Flag_of_the_United_States.svg.png"});
  }else{
    if(row.country_name == "Russia") {
      return Object({co2: row.co2, primary_energy_consumption: row.primary_energy_consumption,
                   flag: "https://upload.wikimedia.org/wikipedia/en/thumb/f/f3/Flag_of_Russia.svg/320px-Flag_of_Russia.svg.png"});
    }else{
      if(row.country_name == "India") {
        return Object({co2: row.co2, primary_energy_consumption: row.primary_energy_consumption,
                   flag: "https://upload.wikimedia.org/wikipedia/commons/thumb/4/41/Flag_of_India.svg/320px-Flag_of_India.svg.png"});
      }else{
        if(row.country_name == "European Union") {
          return Object({co2: row.co2, primary_energy_consumption: row.primary_energy_consumption,
                   flag: "https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/Flag_of_Europe.svg/320px-Flag_of_Europe.svg.png"});
        }else{
          if(row.country_name == "China") {
            return Object({co2: row.co2, primary_energy_consumption: row.primary_energy_consumption,
                   flag: "https://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Flag_of_the_People%27s_Republic_of_China.svg/320px-Flag_of_the_People%27s_Republic_of_China.svg.png"});
          }
        }
      }
    }
  }
}
                                                                          
)
```

```js
rest_of_the_world = Plot.plot({
  width:500,
  height:700,
  marks: [
    Plot.line(except_rest_world2 , {
      x: "primary_energy_consumption", // Bar length based on the value
      y: "co2", // Country name on the y-axis
      z: "country_name",
      stroke: "country_name",
      insetTop: 2,
      insetBottom: 2,
      strokeWidth: d => Math.pow(rocket_year2 - d.year + 1, 0.85),
      strokeOpacity: d => (d.year - rocket_year1)*(1-0.05)/15.0 + 0.05,
      strokeLinejoin : "round",
      title: (d) => `${d.year}`,
    }),
    Plot.image(last_flags_except_world2, {
      x: d=> d.primary_energy_consumption + 600,
      y: "co2",
      src: "flag",
      r: 12,
      preserveAspectRatio: "xMidYMid slice",
      title: "Name"
    }),
    Plot.ruleX([4000]),
    Plot.ruleY([1000]),
  ],
  x: { label: "Primary energy consumption - Measured in terawatt-hours." }, // Label for the facet axis (optional)
  y: { label: "Annual CO₂ emissions (million tonnes)" }, // Remove global y-axis label to avoid redundancy
  grid: true, // Add gridlines for better readability
  facetPadding: 30, // Add space between facets
  height: 800, // Adjust height based on the number of facets
  width, // Adjust the overall width of the plot
  color: {
    domain: domain_countries,
    range: range_colors_countries,
    legend: false
  }
});
```

```js
co2_data_predictions = d3.csv("https://nyc3.digitaloceanspaces.com/owid-public/data/co2/owid-co2-data.csv")
```

```js
our_world_id = d3.csv("https://ourworldindata.org/grapher/continents-according-to-our-world-in-data.csv?v=1&csvType=full&useColumnShortNames=true")
```

```js
co2_country_data = co2_data_predictions.filter(row =>
  our_world_id.some(
    worldRow => worldRow.Entity == row.country && worldRow.Code == row.iso_code
  )
);
```

```js
co2_global_after_2010 = Array.from(d3.rollup(co2_country_data.filter(row => row.year >= 2000), v => d3.sum(v, d => d.total_ghg), d => d.year)).map(row => Object({year: Number(row[0]), co2: row[1]}))
```

```js
world_stopped_tendency = {
  const co2_2020 = co2_global_after_2010.find(row => row.year == 2020).co2
  const co2_2019 = co2_global_after_2010.find(row => row.year == 2019).co2
  const ratio = (co2_2019 - co2_2020)*100/ co2_2020; 
   return Array.from({ length: 11 }, (value, index) => Object({year: (index + 2020),
                                                               co2: co2_2020*Math.pow(1 - ratio/100, index)}));
}
```

```js
optimitistic_area = {
   const reference_year_value = co2_global_after_2010.find(row => row.year == 2019).co2;
   return Array.from({ length: 12 }, (value, index) => Object({year: (index + 2019),
                                                               co2_bottom: reference_year_value*Math.pow(1 - 4.65/100, index),
                                                              co2_top: reference_year_value*Math.pow(1 - 7.6/100, index)}));
}
```

```js
hopeful_area = {
   const reference_year_value = co2_global_after_2010.find(row => row.year == 2019).co2;
   return Array.from({ length: 12 }, (value, index) => Object({year: (index + 2019),
                                                               co2_bottom: reference_year_value*Math.pow(1 - 2.3/100, index),
                                                              co2_top: reference_year_value*Math.pow(1 - 4.65/100, index)}));
}
```

```js
two_degree_area = {
   const reference_year_value = co2_global_after_2010.find(row => row.year == 2019).co2;
   return Array.from({ length: 12 }, (value, index) => Object({year: (index + 2019),
                                                               co2_bottom: reference_year_value*Math.pow(1 - 1.2/100, index),
                                                              co2_top: reference_year_value*Math.pow(1 - 2.3/100, index)}));
}
```

```js
recent_year = d3.max(co2_country_data.map(row => row.year))
```

```js
europe = ["AUT",
"BEL",
"BGR",
"HRV",
"CYP",
"CZE",
"DNK",
"EST",
"FIN",
"FRA",
"DEU",
"GRC",
"HUN",
"IRL",
"ITA",
"LVA",
"LTU",
"LUX",
"MLT",
"NLD",
"POL",
"PRT",
"ROU",
"SVK",
"SVN",
"ESP",
"SWE",
"GBR"]
```

```js
co2_recent_year_country = d3.rollup(co2_country_data.filter(row => row.year == recent_year), v => d3.sum(v, d => d.co2), d => d.iso_code)
```

```js
countries_of_interest = Array.from(co2_recent_year_country).sort((a, b) => b[1] - a[1]).slice(0, 4)
  .map(([key, value]) => key);
```

```js
function country_name_interested(d) {
  if(countries_of_interest.includes(d.iso_code)) {
    return d.country;
  }else{
    if(europe.includes(d.iso_code)) {
      return "European Union";
    }else{
      return "Rest of World";
    }
  }
}
```

```js
latest_values = new Map(Array.from(d3.rollup(co2_country_data.filter(row => row.year == 2023),
                                     v => d3.sum(v, d => d.total_ghg),
                                     d => country_name_interested(d))))
```

```js
last_bar = [Object({country: "Rest of the world", year:2030,co2: latest_values.get("Rest of World")*Math.pow(1 + form_variations.rest_of_world/100, 7), flag: "https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/EarthFlag.svg/320px-EarthFlag.svg.png"}),
            Object({country: "China", year:2030,co2: latest_values.get("China")*Math.pow(1 + form_variations.china/100, 7),
                   flag: "https://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Flag_of_the_People%27s_Republic_of_China.svg/320px-Flag_of_the_People%27s_Republic_of_China.svg.png"}),
           Object({country: "United States", year:2030,co2: latest_values.get("United States")*Math.pow(1 + form_variations.usa/100, 7),
                  flag: "https://upload.wikimedia.org/wikipedia/en/thumb/a/a4/Flag_of_the_United_States.svg/320px-Flag_of_the_United_States.svg.png"}),
           Object({country: "India", year:2030,co2: latest_values.get("India")*Math.pow(1 + form_variations.india/100, 7),
                  flag: "https://upload.wikimedia.org/wikipedia/commons/thumb/4/41/Flag_of_India.svg/320px-Flag_of_India.svg.png"}),
            Object({country: "European Union", year:2030,co2: latest_values.get("European Union")*Math.pow(1 + form_variations.europe_union/100, 7), flag: "https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/Flag_of_Europe.svg/320px-Flag_of_Europe.svg.png"}),
            Object({country: "Russia", year:2030,co2: latest_values.get("Russia")*Math.pow(1 + form_variations.russia/100, 7),
                   flag: "https://upload.wikimedia.org/wikipedia/en/thumb/f/f3/Flag_of_Russia.svg/320px-Flag_of_Russia.svg.png"}),
           ]
```

```js
function calculate_co2_prediction(i) {
  const china = latest_values.get("China")*Math.pow(1 + form_variations.china/100, i);
  const usa = latest_values.get("United States")*Math.pow(1 + form_variations.usa/100, i);
  const russia = latest_values.get("Russia")*Math.pow(1 + form_variations.russia/100, i);
  const europe_union = latest_values.get("European Union")*Math.pow(1 + form_variations.europe_union/100, i);
  const india = latest_values.get("India")*Math.pow(1 + form_variations.india/100, i);
  const rest_of_world = latest_values.get("Rest of World")*Math.pow(1 + form_variations.rest_of_world/100, i);
  return china + usa + russia + europe_union + india + rest_of_world;
}
```

```js
last_bar_cum = {
  const temporal = [];
  for (const [i, row] of last_bar.entries()) {
    if(i>0){
      temporal.push(Object({country: row.country, year: row.year, co2: row.co2 + temporal.at(-1).co2, flag: row.flag}))
    }else{
      temporal.push(row)
    }
  }
  return temporal
}
```

```js
you_hope = {
   return Array.from({ length: 8 }, (value, index) => Object({year: (index + 2023),
                                                               co2: calculate_co2_prediction(index)}));
}
```

```js
domain_countries = ["United States", "China", "India", "Russia", "European Union", "Rest of the world"]
    
```

```js
range_colors_countries = [
        "#0A3161",
        "#cd071e",
      "#FF671F",
      "green",
      "#FFCC00",
  "grey"
      ]
```

```js
function get_color_by_country_name(cn) {
  const indx_name = domain_countries.indexOf(cn);
  return range_colors_countries[indx_name];
}

```

```js
viewof form_variations = Inputs.form({
  europe_union: Inputs.range([-10, 10], {label: "European Union", step: 0.1, value:0}),
  china: Inputs.range([-10, 10], {label: "China", step: 0.1, value:0}),
  usa: Inputs.range([-10, 10], {label: "United States", step: 0.1, value:0}),
  russia: Inputs.range([-10, 10], {label: "Russia", step: 0.1, value:0}),
  india: Inputs.range([-10, 10], {label: "India", step: 0.1, value:0}),
  rest_of_world: Inputs.range([-10, 10], {label: "Rest of the world", step: 0.1, value:0})
})
```

```js
pointerMX = pointerMore(Plot.pointerX)
```

```js
function pointerMore(pointer) {
  return ({ atrest = null, selector = "point", render, ...options } = {}) => {
    const I = new WeakMap(); // Memoize the at rest index for each facet (for performance).

    return pointer({
      ...options,
      render(index, scales, values, dimensions, context, next) {
        const facet = context.getMarkState(this).facets[index.fi ?? 0]; // full index for the current facet
        const { x, x1, x2, y, y1, y2, z, stroke, fill } = values.channels;
        const X = x?.value ?? x2?.value ?? x1?.value;
        const Y = y?.value ?? y2?.value ?? y1?.value;
        const VX = values.x ?? values.x2 ?? values.x1;
        const VY = values.y ?? values.y2 ?? values.y1;
        const Z = z?.value ?? stroke?.value ?? fill?.value;

        // at rest
        if (!I.has(facet)) {
          let select;
          switch (String(atrest).toLowerCase()) {
            case "null":
              select = () => [];
              break;
            case "minx":
              if (!X) throw new Error("missing channel x");
              select = (index) => [d3.least(index, (i) => X[i])];
              break;
            case "maxx":
              if (!X) throw new Error("missing channel x");
              select = (index) => [d3.greatest(index, (i) => X[i])];
              break;
            case "miny":
              if (!Y) throw new Error("missing channel y");
              select = (index) => [d3.least(index, (i) => Y[i])];
              break;
            case "maxy":
              if (!Y) throw new Error("missing channel y");
              select = (index) => [d3.greatest(index, (i) => Y[i])];
              break;
            case "first":
              select = (index) => index.slice(0, 1);
              break;
            case "last":
              select = (index) => index.slice(-1);
              break;
            // TODO top, bottom, left, right… ?
          }
          if (!select) throw new Error(`unsupported atrest method ${atrest}`);
          I.set(facet, select(facet));
        }

        if (index.length === 0) index = I.get(facet);

        // selector
        switch (String(selector).toLowerCase()) {
          case "point":
            break;
          case "before":
          case "lte":
            if (!VX) throw new Error("missing channel x");
            index = facet.filter((i) => VX[i] <= VX[index[0]]);
            break;
          case "lt":
            if (!VX) throw new Error("missing channel x");
            index = facet.filter((i) => VX[i] < VX[index[0]]);
            break;
          case "after":
          case "gte":
            if (!VX) throw new Error("missing channel x");
            index = facet.filter((i) => VX[i] >= VX[index[0]]);
            break;
          case "gt":
            if (!VX) throw new Error("missing channel x");
            index = facet.filter((i) => VX[i] > VX[index[0]]);
            break;
          case "eq":
          case "x":
            if (!VX) throw new Error("missing channel x");
            index = facet.filter((i) => VX[i] == VX[index[0]]);
            break;
          case "y":
            if (!VY) throw new Error("missing channel y");
            index = facet.filter((i) => VY[i] == VY[index[0]]);
            break;
          case "z":
            if (!Z) throw new Error("missing channel z");
            index = facet.filter((i) => Z[i] == Z[index[0]]);
            break;
          default:
            throw new Error(`unsupported selector ${selector}`);
        }

        return render
          ? render(index, scales, values, dimensions, context, next)
          : next(index, scales, values, dimensions, context);
      }
    });
  };
}
```

```js
filtered_data_for_pointer = co2_global_after_2010.filter(d => d.year <= 2019);
```

```js
simulation = {
  const colorScaleHeatmap = d3.scaleSequential()
    .domain([0, 1.4]) // Scale from 0 to 1.4
    .interpolator(d3.interpolateRgbBasis([
      "rgb(255, 240, 220)", // Very light orange, almost white
      "rgb(253, 204, 138)", // Soft orange
      "rgb(252, 141, 89)",  // More saturated orange
      "rgb(227, 74, 51)",   // Intense red-orange
      "rgb(179, 0, 0)"      // Deep red
    ]));
  
  const chart = Plot.plot({
    width,
    height: 480,
    grid: true,
    marginTop: 30,
    marginLeft: 60,
    y: { label: "Global Annual greenhouse gas emissions (million tonnes)" },
    x: { label: "Year", interval: 1 },
    marks: [
       // Smooth curve for aesthetics
      Plot.lineY(co2_global_after_2010, { x: "year", y: "co2", tip: false, strokeWidth: 2, strocke:"black",curve: "natural" }),
      Plot.areaY(co2_global_after_2010.filter(d => d.year < 2020), { 
                x: "year", 
                y: "co2", 
                fill: "black", 
                fillOpacity: 0.05 
              }),
      Plot.ruleX(filtered_data_for_pointer, pointerMX({
        x: "year", atrest: "maxX", stroke: "darkblue", strokeDasharray: "3,3", strokeWidth: 3
      })),
      
      Plot.text(filtered_data_for_pointer, pointerMX({
        x: "year", atrest: "maxX", text: ({ year }) => `Year ${year}:`, fill: "currentColor",
        stroke: "var(--plot-background)", strokeWidth: 12, frameAnchor: "top", dy: -25
      })),
      
      Plot.text(filtered_data_for_pointer, pointerMX({
        x: "year", atrest: "maxX", text: ({ co2 }) => `${Math.round(co2)}M tons of CO2`,
        fill: "currentColor", stroke: "var(--plot-background)", strokeWidth: 12, frameAnchor: "top", dy: -10
      })),
      
      Plot.axisY({
        label: "Annual GHG emissions (M tons)",
        tickFormat: d => d.toFixed(2),
        ticks: 8,
        color: "darkblue",
        anchor: "left",
      }),
      
      Plot.lineY(you_hope, { x: "year", y: "co2", stroke: "red", strokeDasharray: "10,10", strokeWidth: 3, curve: "natural" }),
      
      Plot.areaY(optimitistic_area, { x: "year", y1: "co2_bottom", y2: "co2_top", fill: colorScaleHeatmap(0.5), opacity: 0.4 }),
      Plot.areaY(hopeful_area, { x: "year", y1: "co2_bottom", y2: "co2_top", fill: colorScaleHeatmap(1.0), opacity: 0.4 }),
      Plot.areaY(two_degree_area, { x: "year", y1: "co2_bottom", y2: "co2_top", fill: colorScaleHeatmap(1.4), opacity: 0.4 }),
      
    Plot.ruleX([2019], { 
      stroke: "black", 
      strokeWidth: 2, 
      strokeDasharray: "4 4",
      label: "2019",
      labelAnchor: "top" 
    }),
      
      Plot.barY(last_bar, { x: "year", y: "co2", fill: d => get_color_by_country_name(d.country), rx: 2, padding: 0.2 }),
      
      Plot.image(last_bar_cum, {
        x: d => d.year + 1, y: d => d.co2 - 1000, src: "flag", r: 10,
        preserveAspectRatio: "xMidYMid slice", title: "Name"
      }),
    ]
  });

  const legend = Plot.legend({
    color: {
      type: "ordinal",
      domain: ["1.5ºC Range", "1.8ºC Range", "2ºC Range", "Prediction"],
      range: [
        colorScaleHeatmap(0.5),
        colorScaleHeatmap(1.0),
        colorScaleHeatmap(1.4),
        "blue"
      ],
    },
    legend: true,
  });

  return html`${legend}${chart}`;
}

```

#### Regplot

```js
dataRegPlot = owidCo2Data
  .filter(d => d.year > 1950)
  .filter(d => d.gdp_per_capita != 0 && d.co2_per_capita != 0)
  .filter(d => d.population != 0)

.map(d => ({
    name: d.country,
    year: d.year,
    co2_per_capita: parseInt(d.co2_per_capita), 
    gdp: parseInt(d.gdp), 
    population: parseInt(d.population), 
    gdp_per_capita: Math.round(parseInt(d.gdp/d.population)*100)/100 
     }));

```

```js
viewof year_reg_plot = Scrubber(d3.range(1951, 2023), {loop: false, delay: 300})
```

```js
dataForYear = dataRegPlot.filter(d =>
  d.year === year_reg_plot &&
  d.gdp_per_capita > 2000 &&
  d.co2_per_capita > 2 &&
  d.gdp_per_capita < 100000 && 
  d.co2_per_capita < 30       
);
// filtering for outliers
```

```js
import {Plot} from "@mkfreeman/plot-tooltip"
```

```js
function assign_continent_regplot(data_in, values, field_original) {
  for (var i=0 ; i<data_in.length; i++) {
        data_in[i][field_original] = values[data_in[i]['name']];
    }
return data_in
}
```

```js
assign_continent_regplot(dataForYear, continents_trading_plot, "continent")

```

```js
regression_plot3 = {
  dataForYear.sort((a, b) => a.gdp_per_capita - b.gdp_per_capita);
  const bottom10 = dataForYear.slice(0, 10);
  const top10 = dataForYear.slice(-10);
  const subset = [...bottom10, ...top10];

  function linearRegression(x, y) {
    const n = x.length;
    const meanX = d3.mean(x);
    const meanY = d3.mean(y);
    let num = 0;
    let den = 0;
    for (let i = 0; i < n; i++) {
      num += (x[i] - meanX) * (y[i] - meanY);
      den += (x[i] - meanX) * (x[i] - meanX);
    }
    const slope = num / den;
    const intercept = meanY - slope * meanX;
    return { slope, intercept };
  }

  function movingAverage(arr, windowSize) {
    return arr.map((_, idx, src) => {
      const start = Math.max(0, idx - windowSize + 1);
      const subset = src.slice(start, idx + 1);
      return d3.mean(subset);
    });
  }

  const xVals = dataForYear.map(d => d.gdp_per_capita);
  const yVals = dataForYear.map(d => d.co2_per_capita);

  // Compute regression parameters for the last 5 years using moving average
  const slopes = [];
  const intercepts = [];
  for (let i = 0; i < 5; i++) {
    const { slope, intercept } = linearRegression(xVals, yVals);
    slopes.push(slope);
    intercepts.push(intercept);
  }
  const avgSlope = movingAverage(slopes, 5).pop();
  const avgIntercept = movingAverage(intercepts, 5).pop();

  // Compute standard deviation for regression uncertainty
  const residuals = yVals.map((y, i) => y - (avgSlope * xVals[i] + avgIntercept));
  const stdDev = d3.deviation(residuals);

  const xMin = d3.min(xVals), xMax = d3.max(xVals);

  const extendedXMin = 2500;
  const extendedXMax = 100000
  const yMin = 1;
  const yMax = 25;
  
  // Compute the unclamped regression line values
  const yStart = avgSlope * extendedXMin + avgIntercept;
  const yEnd = avgSlope * extendedXMax + avgIntercept;
  
  // Compute the standard deviation bounds (before clamping)
  const upperBoundStart = yStart + stdDev;
  const lowerBoundStart = yStart - stdDev;
  const upperBoundEnd = yEnd + stdDev;
  const lowerBoundEnd = yEnd - stdDev;
  
  // Compute the clamped midline, ensuring it stays within bounds
  const yStartClamped = Math.min(yMax - stdDev, Math.max(yMin + stdDev, yStart));
  const yEndClamped = Math.min(yMax - stdDev, Math.max(yMin + stdDev, yEnd));
  
  // Maintain the same offset from the clamped midline
  const y1Start = yStartClamped - stdDev;
  const y2Start = yStartClamped + stdDev;
  const y1End = yEndClamped - stdDev;
  const y2End = yEndClamped + stdDev;
  
  // Ensure the area band remains within bounds
  const y1StartFinal = Math.min(yMax, Math.max(yMin, y1Start));
  const y2StartFinal = Math.min(yMax, Math.max(yMin, y2Start));
  const y1EndFinal = Math.min(yMax, Math.max(yMin, y1End));
  const y2EndFinal = Math.min(yMax, Math.max(yMin, y2End));

return Plot.plot({
  width: 800,
  height: 600,
  marks: [
    Plot.dot(subset, {
      x: "gdp_per_capita",
      y: "co2_per_capita",
      r: "population",
      fill: "continent",
      stroke: "continent",
      strokeWidth: 1,
      fillOpacity: 0.4,
      title: (d) => `${d.name}`,
    }),
    Plot.line(
      [
        { x: extendedXMin, y: yStartClamped },
        { x: extendedXMax, y: yEndClamped }
      ],
      { x: "x", y: "y", stroke: "blue", strokeWidth: 3, strokeDasharray: "5,5" }
    ),
    Plot.area(
      [
        { x1: extendedXMin, y1: y1StartFinal, y2: y2StartFinal },
        { x1: extendedXMax, y1: y1EndFinal, y2: y2EndFinal }
      ],
      { x1: "x1", y1: "y1", y2: "y2", fill: "blue", opacity: 0.15 }
    )
  ],
  x: {
    label: "GDP $ per capita",
    ticks: 10,
    type: "log",
    domain: [2500, 100000],
  },
  y: {
    label: "CO₂ kg per capita",
    ticks: 10,
    domain: [1, 25],
  },
  r: { range: [8, 60] },
  color: {
    domain: [
      "Asia", "Europe", "North America", "South America", "Africa", "Oceania",
      "Global Average CO2-GDP Relationship", "Uncertainty Band"
    ],
    range: [
      "#cd071e", "#FFCC00", "#0A3161", "#28a745", "#a020f0", "#ff1493",
      "blue", "rgba(0, 0, 255, 0.15)"
    ],
    legend: true,
  }
});
}
```

#### Energy Source Distribution

```js
import {emissions, Treemap, sectors, combined_data} from "@oriol-bustos/ggg_processing"
```

```js
const top10CountriesArray = [
  "United States",   
  "China",               // Asia - Mayor emisor global de CO₂
  "India",               // Asia - En rápido crecimiento en emisiones
  "Germany",  
  "Russia",              // Europa/Asia - Gran productor de energía fósil
  "Brazil",              // América del Sur - Emisiones por deforestación
  "South Africa",        // África - Mayor emisor del continente
  "Saudi Arabia",        // Medio Oriente - País petrolero con altas emisiones
  "Australia",           // Oceanía - Alto consumo per cápita de CO₂
  "Japan",               // Asia - Potencia industrial con grandes emisiones
  "Trinidad and Tobago"
];
```

```js
viewof selected_country_energy_sources = Inputs.select(top10CountriesArray, {value: "China", label: "Select Country: "})
```

```js
viewof selected_window_year_energy_sources = interval([1951, 2023], {
  step: 1,
  value: [1951, 2023],
  label: 'Select an Interval to Show',
})
```

```js
viewof selected_year_energy_sources = Inputs.range([1969, 2023], {value: 2000, step: 1, label: "Individual Year for the Squared Map: "})
```

```js
const emissionsCountry = emissions[selected_country_energy_sources].data
```

```js
const emissionsCountryStackedProcessed = emissionsCountry.flatMap(d => {
  const total = (d.cement_co2_per_capita || 0) +
                (d.oil_co2_per_capita || 0) +
                (d.gas_co2_per_capita || 0) +
                (d.flaring_co2_per_capita || 0) +
                (d.coal_co2_per_capita || 0) +
                (d.other_co2_per_capita || 0);
  
  return [
    { year: d.year, source: "Cement", value: d.cement_co2_per_capita, percentage: (d.cement_co2_per_capita / total) },
    { year: d.year, source: "Oil", value: d.oil_co2_per_capita, percentage: (d.oil_co2_per_capita / total) },
    { year: d.year, source: "Gas", value: d.gas_co2_per_capita, percentage: (d.gas_co2_per_capita / total) },
    { year: d.year, source: "Flaring", value: d.flaring_co2_per_capita, percentage: (d.flaring_co2_per_capita / total)},
    { year: d.year, source: "Coal", value: d.coal_co2_per_capita, percentage: (d.coal_co2_per_capita / total)},
    { year: d.year, source: "Other Sources", value: d.other_co2_per_capita, percentage: (d.other_co2_per_capita / total)}
  ];
});
```

```js
const emissionsFilteredStreamgraph = emissionsCountryStackedProcessed
.filter(d => d.year > selected_window_year_energy_sources[0])
.filter(d => d.year < selected_window_year_energy_sources[1])
```

```js
const offsetStacked = null
```

```js
const stacked_plot = Plot.plot({
  marginLeft: 50,
  marginBottom: 40,
  width,
  y: {
    grid: true,
    label: "CO2 emitted per capita",
    percent: true,
  },
  x: {
    label: "Year",
    tickFormat: d => `${d}`,
  },
  color: {
    legend: true,
    range: [
      "#c8c8c8",  // cement (light gray)
      "#4d4d4d",  // coal (charcoal gray)
      "#ffd1a8",  // flaring (light peach)
      "#f78bbf",  // gas (soft pink)
      "#f77b47",  // oil (light coral)
      "#ffec8b"   // other sources (light yellow)
    ]
  },
  marks: [
    Plot.areaY(
      emissionsFilteredStreamgraph,
      Plot.stackY({ offsetStacked, reverse: false }, {
        x: "year",
        y: "value",
        fill: "source",
        fillOpacity: 0.99,
        stroke:"source",
        title: d => `Source: ${d.source}
Year: ${d.year}
CO2 emitted per capita: ${Math.round(d.value * 1000) / 1000}
Represents: ${Math.round(d.percentage * 100)}%`,
      })
    ),
    // Add vertical marker line
    Plot.ruleX([selected_year_energy_sources], {
      stroke: "black",
      strokeWidth: 2,
      strokeDasharray: "4 4",  // Dashed line for better visibility
      label: selected_year_energy_sources,
    })
  ]
});

```

```js
someCountryCodes = [
  { name: "United States", code: "USA" },
  { name: "China", code: "CHN" },
  { name: "India", code: "IND" },
  { name: "Germany", code: "DEU" },
  { name: "Russia", code: "RUS" },
  { name: "Brazil", code: "BRA" },
  { name: "South Africa", code: "ZAF" },
  { name: "Saudi Arabia", code: "SAU" },
  { name: "Australia", code: "AUS" },
  { name: "Japan", code: "JPN" },
  { name: "Trinidad and Tobago", code:"TTO"}
];
```

```js
const countryMap = someCountryCodes.reduce((map, country) => {
  map[country.name] = country.code;
  return map;
}, {});
```

```js
const someCountryCode = countryMap[selected_country_energy_sources];
```

```js
const data_for_tree= combined_data[selected_year_energy_sources][someCountryCode];
```

```js
const total_emissions = sectors.reduce((total, sector) => {
  const emissions = data_for_tree[sector];
  return total + (typeof emissions === 'number' ? emissions : 0);
}, 0);
```

```js
const co2_emissions = sectors.map(sector => {
  const emissions = data_for_tree[sector];
  const percentage = (emissions / total_emissions) * 100;  // Calcular el porcentaje
  return {
    Sector: sector,                // El nombre del sector
    CO2_Emissions: emissions,      // Emisiones de CO2
    Percentage: percentage.toFixed(2)  // Porcentaje con 2 decimales
  };
});
```

```js
function createSectorColorMap() {
  const sectorColors = {};

  sectorColors["oil_co2"] = "#f77b47";      // Oil (light coral)
  sectorColors["gas_co2"] = "#f78bbf";      // Gas (soft pink)
  sectorColors["coal_co2"] = "#4d4d4d";     // Coal (charcoal gray)
  sectorColors["cement_co2"] = "#c8c8c8";   // Cement (light gray)
  sectorColors["flaring_co2"] = "#ffd1a8";  // Flaring (light peach)
  sectorColors["land_use_co2"] = "#ffec8b"; // Other sources (light yellow)

  return sectorColors;
}
```

```js
const sectorColorMap = createSectorColorMap();
```

```js
treemap_chart = Treemap(co2_emissions, {
  path: (d) => d?.Sector,
  value: (d) => d?.Percentage,
  group: (d) => d?.Sector,
  label: (d, n) =>
    [
      d.Sector,
      `${n.value.toLocaleString("en")} %`
    ].join("\n"),
  title: (d, n) => `${d.Sector}\n${n.value.toLocaleString("en")} %`,
  tile: d3.treemapBinary,
  width: 700,
  height: 500,
  colors: co2_emissions.map(d => sectorColorMap[d.Sector] || "#ccc") // Assign colors dynamically
});
```

#### Radar plot

```js
import {exclusions, co2Keys}  from "@oriol-bustos/ggg_processing"
```

```js
richestAndPoorestByYear = Array.from(
  d3.group(
    // Filter for data from 1850 onward and exclude non-country entries
    owidCo2Data.filter(d => d.year >= 1850 && !exclusions.includes(d.country)),
    d => d.year
  ),
  ([year, records]) => {
    // Sort countries by GDP (descending order)
    const sortedByGDP = records.sort((a, b) => b.gdp - a.gdp);

    return {
      year: +year,
      richest: sortedByGDP.slice(0, 10), // Top 10 richest with all info
      poorest: sortedByGDP.slice(-10),  // Bottom 10 poorest with all info
      middle10: sortedByGDP.slice(
        Math.floor((sortedByGDP.length - 10) / 2),
        Math.floor((sortedByGDP.length - 10) / 2) + 10
      ),  
      topQuartile: sortedByGDP.slice(
        0, Math.ceil(sortedByGDP.length / 4)
      ),                                           // Top 25% richest
      bottomQuartile: sortedByGDP.slice(
        Math.floor(sortedByGDP.length * 3 / 4)
      )
    };
  }
);

```

```js
reshaped_radar_data = [];
```

```js
richestAndPoorestByYear.forEach(({ year, richest, poorest }) => {
  const yearPoints = []; // Temporary array to collect points for a specific year

  co2Keys.forEach((co2Key) => {
    const richValues = richest.map((r) => Number(r[co2Key]) || 0);
    const richAvg =
      richValues.reduce((sum, val) => sum + val, 0) / richValues.length || 0;

    const poorValues = poorest.map((p) => Number(p[co2Key]) || 0);
    const poorAvg =
      poorValues.reduce((sum, val) => sum + val, 0) / poorValues.length || 0;

    // Push "rich" object
    yearPoints.push({
      year,
      name: "rich",
      key: co2Key,
      value: richAvg
    });

    // Push "poor" object
    yearPoints.push({
      year,
      name: "poor",
      key: co2Key,
      value: poorAvg
    });
  });

  // Calculate total sum for "rich" points only
  const totalSumRich = yearPoints
    .filter((point) => point.name === "rich")
    .reduce((sum, point) => sum + point.value, 0) || 1;

  // Calculate total sum for "poor" points only
  const totalSumPoor = yearPoints
    .filter((point) => point.name === "poor")
    .reduce((sum, point) => sum + point.value, 0) || 1;

  // Add `pct` field to each point, relative to the group total
  yearPoints.forEach((point) => {
    if (point.name === "rich") {
      point.pct = Math.round((point.value / totalSumRich) * 100);
    } else if (point.name === "poor") {
      point.pct = Math.round((point.value / totalSumPoor) * 100);
    }
  });

  // Push the year points into the main points array
  reshaped_radar_data.push(...yearPoints);
});

```

```js
viewof yearRadar = Scrubber(d3.range(1900, 2023), {loop: false, delay: 150})
```

```js
filteredPoints = reshaped_radar_data
  .filter(d => d.year === yearRadar)
  .map(d => ({
    name: d.name,
    key: d.key === "gas_co2_per_capita" ? "Gas" :
          d.key === "oil_co2_per_capita" ? "Oil" :
          d.key === "coal_co2_per_capita" ? "Coal" : d.key,
    value: d.pct / 100
  }));

```

```js
longitude = d3.scalePoint(new Set(Plot.valueof(filteredPoints, "key")), [180, -180]).padding(0.5).align(1)
```

```js
radar_plot = Plot.plot({
  marginLeft: 50,
  marginBottom: 40,
  width: 450,
  className: "radar-plot", // Add a unique class
  projection: {
    type: "azimuthal-equidistant",
    rotate: [0, -90],
    domain: d3.geoCircle().center([0, 90]).radius(1)()
  },
  color: {
    legend: true,
    domain: ["rich", "poor"],
    range: ["red", "blue"],
    tickFormat: d => d === "rich" ? "Top 10 Richest Countries" : "Top 10 Poorest Countries"
  },
  marks: [
    // grey discs
    Plot.geo([0.9,0.8,0.7,0.6, 0.5, 0.4, 0.3, 0.2, 0.1], {
      geometry: (r) => d3.geoCircle().center([0, 90]).radius(r)(),
      stroke: "black",
      fill: "black",
      strokeOpacity: 0.3,
      fillOpacity: 0.03,
      strokeWidth: 0.5
    }),

    // white axes
    Plot.link(longitude.domain(), {
      x1: longitude,
      y1: 90 - 0.95,
      x2: 0,
      y2: 90,
      stroke: "black",
      strokeOpacity: 0.4,
      strokeWidth: 2
    }),

    // tick labels
    Plot.text([0.1,0.2,0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9], {
      x: -45,
      y: (d) => 90 + d,
      dx: 5,
      textAnchor: "start",
      text: (d) => `${100 * d}%`,
      fill: "currentColor",
      stroke: "white",
      fontSize: 8
    }),

    // axes labels
    Plot.text(longitude.domain(), {
      x: longitude,
      y: 90 - 1,
      dx: 4,
      text: Plot.identity,
      lineWidth: 5
    }),

    // areas
    Plot.area(filteredPoints, {
      x1: ({ key }) => longitude(key),
      y1: ({ value }) => 90 - value,
      x2: 0,
      y2: 90,
      fill: "name",
      stroke: "name",
      curve: "cardinal-closed"
    }),

    // points
    Plot.dot(filteredPoints, {
      x: ({ key }) => longitude(key),
      y: ({ value }) => 90 - value,
      fill: "name",
      stroke: "white"
    }),

    // interactive labels
    Plot.text(
      filteredPoints,
      Plot.pointer({
        x: ({ key }) => longitude(key),
        y: ({ value }) => 90 - value,
        text: (d) => `${(100 * d.value).toFixed(0)}%`,
        textAnchor: "start",
        dx: 4,
        fill: "currentColor",
        stroke: "white",
        maxRadius: 10
      })
    ),

    // interactive opacity on the areas
    () =>
    svg`<style>
      .radar-plot g[aria-label=area] path {
        fill-opacity: 0.1; 
        transition: fill-opacity .2s;
      }
      .radar-plot g[aria-label=area]:hover path:not(:hover) {
        fill-opacity: 0.05; 
        transition: fill-opacity .2s;
      }
      .radar-plot g[aria-label=area] path:hover {
        fill-opacity: 0.3; 
        transition: fill-opacity .2s;
      }
    </style>`
  ]
})
```

#### Trading

```js
import {continents as continents_trading_plot} from "@oriol-bustos/ggg_processing"
```

```js
viewof selected_year_trading = Scrubber(d3.range(1990, 2023), {loop: false, delay: 200})
```

```js
function assign_continent(data_in, values, field_original) {
  for (var i=0 ; i<data_in.length; i++) {
        data_in[i][field_original] = values[data_in[i]['id']];
    }
return data_in
}
```

```js
data_trading = (
  await fetch(
    "https://nyc3.digitaloceanspaces.com/owid-public/data/co2/owid-co2-data.json"
  )
).json()
```

```js
map_data_trading = Object.entries(data_trading).map(([key, value]) => ([...value.data.map(d => ({id: key, ...d}))]))
```

```js
flat_map_data_trading = map_data_trading.flat()
```

```js
assign_continent(flat_map_data_trading, continents_trading_plot, "continent")
```

```js
clean_trading_data = new Promise(resolve => {
    setTimeout(() => {
        resolve(flat_map_data_trading.filter(d => d.continent !== undefined && d.year >= 1920));
    }, 5000); // Adjust delay if needed
});

```

```js
filtered_emissions = clean_trading_data.filter(d => d.year == selected_year_trading)
```

```js
trading_plot = Plot.plot({
  title:"Emissions per capita vs. Traded CO2",
    color: {
domain: ["Asia", "Europe", "North America", "South America", "Africa", "Oceania"],
range: ["#cd071e", "#FFCC00", "#0A3161", "#28a745", "#a020f0", "#ff1493"],
    legend: true
  },
    y: {
    grid: false,
    type: "log",
    domain: [0.01,100],
    label : "CO2 per capita"
    },
    x: {
    grid: false,
    domain: [-2000,2000],
    label : "Traded CO2"
    },
  marks: [
    Plot.dot(filtered_emissions,
             {x: "trade_co2",
              y: "co2_per_capita",
              r:"population",
              stroke: "continent", 
              fill: "continent", 
              fillOpacity: 0.4,
              title: (d) => d.id 
             }
            )
  ]
})
```

```js
g10 = [
  "Germany", "France", "United Kingdom","Italy",  // Major European signatories
  "USA", "Canada", // North America (USA rejoined in 2021)
  "Sweden", "Switzerland", // Strong environmental commitments
  "Belgium",
  "Japan", "Netherlands"
];
```

```js
total_traded_co2_china = Math.round(
  filtered_emissions
    .filter(d => d.id === "China") // Filter for China only
    .map(d => d.trade_co2)
    .filter(d => d !== null && d !== undefined) // Ensure valid values
    .reduce((sum, d) => sum + d, 0)
);

```

```js
total_traded_co2_paris = Math.round(
  filtered_emissions
    .filter(d => g10.includes(d.id)) // Keep only selected countries
    .map(d => d.trade_co2)
    .filter(d => d !== null && d !== undefined) // Ensure valid values
    .reduce((sum, d) => sum + d, 0)
);
```

## Emissions nexto Trading

```js
aggregatedData = Array.from(
  d3.rollup(
    clean_trading_data,
    v => d3.sum(v, d => d.co2),
    d => d.continent,
    d => d.year
  ),
  ([continent, yearMap]) => Array.from(
    yearMap,
    ([year, avg_co2]) => ({ continent, year, co2: avg_co2 })
  )
).flat();

```

```js
worldData = Array.from(
  d3.rollup(
    clean_trading_data,
    v => d3.sum(v, d => d.co2),
    d => d.year
  ),
  ([year, total_co2]) => ({ continent: "World", year, co2: total_co2 })
);

```

```js
aggregatedData.forEach(d => {
  d.year = +d.year; // ensure it’s numeric
});

```

```js
primerplot = Plot.plot({
  width: 800,
  height: 420,
  marginRight: 50,
  marginTop: 30,
  title:"Total Emissions By Continent",
  grid: true,
  marks: [
    Plot.ruleX(aggregatedData, pointerMX({ x: "year", atrest: "maxX", strokeDasharray: "4,4", strokeWidth: 3 })),
    // Lines for each continent:
    Plot.lineY(aggregatedData, {
      x: "year",
      y: "co2",
      z: "continent",
      stroke: "continent",
      strokeWidth: 2,
      curve: "natural", // Smooth curve for aesthetics
      tip: false,
    }),
      Plot.areaY(aggregatedData, {
      x: "year",
      y1:0,
      y2: "co2",
      z: "continent",
      fill: "continent",
      fillOpacity: 0.15,
      tip: false,
    }),


Plot.tip(
  aggregatedData,
  Plot.pointerX(
    Plot.binX(
      {
        // Instead of returning the entire array v => v,
        // build a readable string
        title: (bin) =>
          bin.map(
            (d) => `${d.continent} CO2: ${Math.round(d.co2,0)}M tons, `
          ).join("\n")
      },
      {
        x: "year",
        thresholds: 200
      }
    )
  )
)

  ],
  x: { label: "Year" },
  y: {
    axis: "right",
    label: "Total CO2 emissions"
  },
  color: {
    domain: ["Asia", "Europe", "North America", "South America", "Africa", "Oceania", "World"],
    range: ["#cd071e", "#FFCC00", "#0A3161", "#28a745", "#a020f0", "#ff1493", "#000000"],
    legend: true
  },
});

```

```js
continentColors={// Define the color mapping (same as your legend)
const continentColors = {
  Asia: "#cd071e",
  Europe: "#FFCC00",
  "North America": "#0A3161",
  "South America": "#28a745",
  Africa: "#a020f0",
  Oceania: "#ff1493",
  World: "#000000"};
  return continentColors
};
```

```js
segonplot = Plot.plot({
  width: 1000,
  height: 250,
  marginRight: 50,
  marginTop: 30,
  style: {
    background: "white", // Dark background for a sleek look
    fontFamily: "Arial, sans-serif",
  },
  grid: true,
  marks: [
    Plot.ruleX(worldData, pointerMX({ x: "year", atrest: "maxX", strokeDasharray: "4,4", strokeWidth: 3 })),
    Plot.tip(
      worldData,
      Plot.pointerX(
        Plot.binX(
          {
            // Instead of returning the entire array v => v,
            // build a readable string
            title: (bin) =>
              bin.map(
                (d) => `${d.continent} CO2: ${Math.round(d.co2,0)}M tons, `
              ).join("\n")
          },
          {
            x: "year",
            thresholds: 200
          }
        )
      )
    ),
    // Line for the world (sum of all continents)
    Plot.lineY(worldData, {
      x: "year",
      y: "co2",
      strokeWidth: 5,
      strokeOpacity: 0.8, // Slight opacity for blending effect
      curve: "natural", // Smooth curve for aesthetics
     // title: (d) => d.year
    }),
  ],
  x: { label: "Year", tickSize: 6, tickPadding: 8, fontSize: 14 },
  y: {
    axis: "right",
    label: "Total CO2 Emissions",
    tickSize: 6,
    tickPadding: 8,
    fontSize: 14,
  },
});

```

```js

```

#### Historic

```table

```

```js
temperature_over_time = {
  const container = d3.create("div");
      
  const width = 1200;
  const height = 500;
  const margin = { top: 50, right: 80, bottom: 50, left: 80 };

  // Create controls container
  const controls = d3.create("div")
    .style("display", "flex")
    .style("alignItems", "center")
    .style("gap", "10px")
    .style("margin-bottom", "10px");
                         
  // Stop/Resume button
  const toggleButton = document.createElement("button");
  toggleButton.textContent = "Stop";
  toggleButton.style.borderRadius = "5px";
  toggleButton.style.backgroundColor = "green";
  toggleButton.style.color = "white";
  toggleButton.style.border = "none";
  toggleButton.style.padding = "5px 10px";
  controls.node().appendChild(toggleButton);

  // Speed slider label
  const speedLabel = document.createElement("span");
  speedLabel.textContent = "Speed:";
  controls.node().appendChild(speedLabel);

  // Speed slider input
  const speedSlider = document.createElement("input");
  speedSlider.type = "range";
  speedSlider.min = "1";      
  speedSlider.max = "1000";    
  speedSlider.value = "800";    
  controls.node().appendChild(speedSlider);

  container.append(() => controls.node());

  // Create SVG element
  const svg = d3.create("svg")
    .attr("width", width)
    .attr("height", height);
  container.append(() => svg.node());

  // Title
  svg.append("text")
    .attr("x", width / 2)
    .attr("y", 15)
    .attr("text-anchor", "middle")
    .attr("font-size", 18)
    .attr("font-weight", "bold")
    .text("Temperature Deviation from 20th-Century Average (ºC) By Year");
                         
function generateBandChart(data, currentYear) {
  const startYear = d3.min(data, d => d.year);
  const endYear = Math.min(currentYear, d3.max(data, d => d.year));
  const filteredData = data.filter(d => d.year >= startYear && d.year <= endYear);

  const xScale = d3.scaleLinear()
    .domain([startYear, endYear])
    .range([margin.left, width - margin.right]);
  const yScale = d3.scaleLinear()
    .domain([-1.4, 1.4])
    .range([height - margin.bottom, margin.top]);

  // --- Generate tick values ---
  // 1. Get default ticks for years below 1400.
  let tickValues = xScale.ticks().filter(t => t < 1400);
  
  // 2. Generate custom ticks for years 1400 and above.
  const splitYear = 1850;
  if (endYear >= 1400) {
    if (endYear <= splitYear) {
      // For years between 1400 and 1850, tick every 50 years.
      for (let t = 1400; t <= endYear; t += 50) {
        tickValues.push(t);
      }
    } else {
      // From 1400 up to 1850, every 50 years.
      for (let t = 1400; t < splitYear; t += 50) {
        tickValues.push(t);
      }
      // Ensure 1850 is included.
      tickValues.push(splitYear);
      // From 1850 onwards, every 10 years.
      for (let t = splitYear + 50; t <= endYear; t += 50) {
        tickValues.push(t);
      }
    }
  }
  
  // Remove duplicates and sort the ticks.
  tickValues = Array.from(new Set(tickValues)).sort((a, b) => a - b);
  
  // --- Clear previous chart elements ---
  svg.selectAll("path, g.axis, .band-line, text.axis-label").remove();

  // --- Create the x axis using custom tick values ---
  const xAxis = d3.axisBottom(xScale)
    .tickValues(tickValues)
    .tickFormat(d3.format("d"));
  svg.append("g")
    .attr("class", "axis")
    .attr("transform", `translate(0,${height - margin.bottom})`)
    .call(xAxis);
  svg.append("text")
    .attr("class", "axis-label")
    .attr("x", width / 2)
    .attr("y", height - 10)
    .attr("text-anchor", "middle")
    .attr("font-size", 12)
    .text("Year");

  // --- Create the y axis ---
  const yAxis = d3.axisLeft(yScale);
  svg.append("g")
    .attr("class", "axis")
    .attr("transform", `translate(${margin.left},0)`)
    .call(yAxis);
  svg.append("text")
    .attr("class", "axis-label")
    .attr("x", -(height / 2))
    .attr("y", 20)
    .attr("text-anchor", "middle")
    .attr("font-size", 12)
    .attr("transform", "rotate(-90)")
    .text("Temperature Anomaly (°C)");

  // --- Draw areas for anomalies ---
  const dataBelow = filteredData.map(d => ({ year: d.year, anomaly: d.anomaly < 0 ? d.anomaly : 0 }));
  const dataAbove = filteredData.map(d => ({ year: d.year, anomaly: d.anomaly > 0 ? d.anomaly : 0 }));

  const areaBelow = d3.area()
    .x(d => xScale(d.year))
    .y0(yScale(0))
    .y1(d => yScale(d.anomaly));
  const areaAbove = d3.area()
    .x(d => xScale(d.year))
    .y0(yScale(0))
    .y1(d => yScale(d.anomaly));

  svg.append("path")
    .datum(dataBelow)
    .attr("fill", "blue")
    .attr("opacity", 0.5)
    .attr("d", areaBelow);
  svg.append("path")
    .datum(dataAbove)
    .attr("fill", "red")
    .attr("opacity", 0.5)
    .attr("d", areaAbove);

  // --- Draw the anomaly line ---
  const line = d3.line()
    .x(d => xScale(d.year))
    .y(d => yScale(d.anomaly));
  svg.append("path")
    .datum(filteredData)
    .attr("class", "band-line")
    .attr("fill", "none")
    .attr("stroke", "#333")
    .attr("stroke-width", 1.5)
    .attr("d", line);
}



  const minYear = d3.min(temperature_historic, d => d.year);
  const maxYear = d3.max(temperature_historic, d => d.year);
  let currentYear = minYear;
  let isRunning = true;
  let animationInterval;

  function getDelay() {
    return +speedSlider.max - (+speedSlider.value) + (+speedSlider.min);
  }

  function startAnimation() {
    const delay = getDelay();
    animationInterval = setInterval(() => {
      generateBandChart(temperature_historic, currentYear);
      
      // If we've reached the last year, stop the animation.
      if (currentYear >= maxYear) {
        clearInterval(animationInterval);
        isRunning = false;
        toggleButton.textContent = "Resume";
        toggleButton.style.backgroundColor = "red";
        return;
      }
      
      // Determine the next year increment
      let nextYear;
      if (currentYear >= 1850) {
        nextYear = currentYear + 1;
      } else if (currentYear >= 1700) {
        nextYear = currentYear + 4;
      } else {
        nextYear = currentYear + 10;
      }
      // Ensure we do not exceed maxYear
      currentYear = nextYear > maxYear ? maxYear : nextYear;
    }, delay);
  }

  // Consolidated toggle button listener
  toggleButton.addEventListener("click", () => {
    if (isRunning) {
      clearInterval(animationInterval);
      isRunning = false;
      toggleButton.textContent = "Resume";
      toggleButton.style.backgroundColor = "red";
    } else {
      // Reset to the beginning if the last year was reached
      if (currentYear >= maxYear) {
        currentYear = minYear;
      }
      isRunning = true;
      toggleButton.textContent = "Stop";
      toggleButton.style.backgroundColor = "green";
      startAnimation();
    }
  });

  // Speed slider listener to update the delay if running
  speedSlider.addEventListener("input", () => {
    if (isRunning) {
      clearInterval(animationInterval);
      startAnimation();
    }
  });

  // Initial start
  startAnimation();

  container.append(() => svg.node());
  container.append(() => controls.node());

  controls
    .style("display", "flex")
    .style("justify-content", "center")  
    .style("align-items", "center")
    .style("gap", "10px")
    .style("margin-top", "10px");        

  const chart = container.node();
  return chart;
}

```

#### Thermometer

```js
margin = ({top: 40, bottom: 20, left: 20, right: 20});
```

```js
thermometer = {
  const container = d3.select(DOM.svg(500+margin.left+margin.right, 
                                      400+margin.top+margin.bottom))
 
  const buttonColor = "#696969";
  const titleFontSize = "16px";
  const font = "system-ui";
  const instructionFontSize = "14px";
  const highlightColor = "#C68400";
    
  const tempGroup = container
       .append("g")
         .attr("transform", "translate(" + margin.left + "," + margin.top + ")") 
  
  const thermometerX = 150;
  const thermometerY = 40;
  
  const thermometer = tempGroup.append("image")
                          .attr('xlink:href', await FileAttachment("thermometer.png").url())
                          .attr("x", thermometerX) 
                          .attr("y", thermometerY)
                          .attr("height", "340px")
                          .attr("width", "100.8902px")
                          .attr("src", await FileAttachment("thermometer.png").url())
                          .classed("in-progess", false)
                     
  const mercuryCircle = tempGroup.append("circle")
                          .attr("cx", thermometerX + 50.5)
                          .attr("cy", thermometerY + 290)
                          .attr("r", 35)
                          .attr("fill", "#ff0000")
                          
  const tempTitle = tempGroup.append("text")
                           .text("Cumulative temperature increase due to GHG")
                           .attr("x", thermometerX-90)
                           .attr("y", 0)
                           .style("font-size", 14)
                           .style("fill", "black")
                           .style("font-family", font)
                           .style("text-anchor", "start")
  
    
  const tempYear = tempGroup.append("text")
                           .text("2023")
                           .attr("x", thermometerX + 50)
                           .attr("y", thermometerY - 10)
                           .style("font-size", 16)
                           .style("fill", buttonColor)
                           .style("font-family", font)
                           .style("text-anchor", "middle")
    
   const tick4C = tempGroup.append("text")
                           .text("2.0°C")
                           .attr("x", thermometerX)
                           .attr("y", thermometerY + 79)
                           .style("font-size", instructionFontSize)
                           .style("fill", buttonColor)
                           .style("font-family", font)
                           .style("text-anchor", "end")
   
   const tick3C = tempGroup.append("text")
                           .text("1.5°C")
                           .attr("x", thermometerX)
                           .attr("y", thermometerY + 126)
                           .style("font-size", instructionFontSize)
                           .style("fill", buttonColor)
                           .style("font-family", font)
                           .style("text-anchor", "end")                  

   
   const tick2C = tempGroup.append("text")
                           .text("1.0°C")
                           .attr("x", thermometerX)
                           .attr("y", thermometerY + 173)
                           .style("font-size", instructionFontSize)
                           .style("fill", buttonColor)
                           .style("font-family", font)
                           .style("text-anchor", "end") 
   
   const targetLimit = tempGroup.append("text")
                           .text("Current")
                           .attr("x", thermometerX + 105)
                           .attr("y", thermometerY + 100)
                           .style("font-size", instructionFontSize)
                           .style("fill", highlightColor)
                           .style("font-family", font)
                           .style("text-anchor", "middle") 
   
   const tick1C = tempGroup.append("text")
                           .text("0.5°C")
                           .attr("x", thermometerX)
                           .attr("y", thermometerY + 220)
                           .style("font-size", instructionFontSize)
                           .style("fill", buttonColor)
                           .style("font-family", font)
                           .style("text-anchor", "end")   
      
   
   const tempIncreaseValue = tempGroup.append("text")
                           .text("+1.7")
                           .attr("x", thermometerX + 49)
                           .attr("y", thermometerY + 100)
                           .style("font-size", "13px")
                           .style("fill", highlightColor)
                           .style("font-family", font)
                           .style("text-anchor", "middle")  
                            .style("font-weight", "Bold")
    
    const mercuryRiseRed = tempGroup.append("rect")
                .attr("x", thermometerX + 40.5)
                .attr("y", thermometerY + 211 - 45)
                .attr("width", 20)
                .attr("height", 0)
                .style("fill", "firebrick") 
                //.style("visibility", "hidden")
   
   const mercuryRiseGreen2 = tempGroup.append("rect")
                .attr("x", thermometerX + 40.5)
                .attr("y", thermometerY + 211)
                .attr("width", 20)
                .attr("height", 0)
                .style("fill", "#82A868") 
                //.style("visibility", "hidden")
   
   const mercuryRiseGreen = tempGroup.append("rect")
                .attr("x", thermometerX + 40.5)
                .attr("y", thermometerY + 102)
                .attr("width", 20)
                .attr("height", 200)
                .style("fill", "#ff0000") 
   
  
   
   const ticks = tempGroup.append("text")
                           .text("- - - -")
                           .attr("x", thermometerX + 50)
                           .attr("y", thermometerY + 165)
                           .style("font-size", "17px")
                           .style("fill", highlightColor)
                           .style("font-family", font)
                           .style("text-anchor", "middle") 
                           .style("font-weight", "Bold")
                           .style("visibility", "hidden")
  

   const resultMessageA = tempGroup.append("text")
                              .style("visibility", "hidden")
                              .style("font-family", font)
                               .style("font-size", "20px")
   
   const resultMessageB = tempGroup.append("text")
                              .style("visibility", "hidden")
                              .style("font-family", font)
                               .style("font-size", instructionFontSize)

  return container.node()
}
```

#### Triple World Map

```js
world = FileAttachment("world@1.json").json()
```

```html
<style>
  .box {
        display: flex;
        flex-wrap: wrap;
    }
</style>
```

```js
indicator = "co2"
```

```js
import {triple_world_import_map, bertin} from "@oriol-bustos/ggg_processing"
```

```js
data_triple_world_json = d3.json("https://nyc3.digitaloceanspaces.com/owid-public/data/co2/owid-co2-data.json")
```

```js
map_data_triple_world_json = Object.entries(emissions).map(([key, value]) => ([...value.data.map(d => ({id: key, ...d}))]))
```

```js
flat_map_data_triple_world_json = map_data_triple_world_json.flat()
```

```js
data_triple_world_json_iso = Object.entries(emissions).map(([key, value]) => ([{id: key, ...value}]))
```

```js
flat_data_triple_world_json_iso = data_triple_world_json_iso.flat()
```

```js
flat_data_triple_world_json_iso.forEach(obj => {
  delete obj.data;
});
```

```js
merge_trading_triple_data = flat_map_data_triple_world_json.reduce((acc, obj) => {
  const matchingObj = flat_data_triple_world_json_iso.find(o => o.id === obj.id);
  acc.push(Object.assign({}, obj, matchingObj));
  return acc;
}, []);
```

```js
viewof selected_year_triple_map = Scrubber(d3.range(1950, 2023), {loop: false, delay: 200})
```

```js
accessor = new Map([
  [
    "co2",
    {
      col: "#d73027",  // Darker red for main fill
      col2: "#f46d43", // Lighter red for secondary color
      max: d3.max(flat_map_data_trading.map((d) => +d.co2)),
      title: "C02"
    }
  ],
  [
    "gdp",
    {
      col: "#fee08b",  // Optional: Keep a different color for GDP if needed
      col2: "#d73027",
      max: d3.max(flat_map_data_trading.map((d) => +d.gdp)),
      title: "GDP"
    }
  ]
])

```

```js
emission_by_year = merge_trading_triple_data.filter((d) => d.year == selected_year_triple_map)
```

```js
emission_filtered = emission_by_year.filter((d) => typeof d.iso_code !== 'undefined')
```

```js
geodata = bertin.merge(world, "ISO3", emission_filtered, "iso_code")
```

```js
viewof triple_world_map = bertin.draw({
  params: { projection: "Eckert3", width: 700, background: "white" },
  layers: [
    {
      type: "bubble",
      geojson: geodata,
      viewof: true,
      values: indicator,
      fill: accessor.get(indicator).col,
      k: 40,
      fixmax: accessor.get(indicator).max,
      leg_x: 40,
      leg_y: 170,
      leg_round: -2,
      leg_title: `${accessor.get(indicator).title} in ${selected_year_triple_map}`,
      tooltip: "$NAMEen"
    },
    { geojson: geodata, fill: "#ccc", fillOpacity: 0.85, stroke: "none" },
  ]
})
```

#### chart 2

```js
worlddata = d3
    .rollups(
      merge_trading_triple_data,
      (v) => d3.sum(v, (d) => d[indicator]),
      (d) => d.year
    )
    .map((d) => ({ id: +d[0], value: d[1] }));
```

```js
chart2data = {
  let worlddata = d3
    .rollups(
      merge_trading_triple_data,
      (v) => d3.sum(v, (d) => +d[indicator]),
      (d) => d.year
    )
    .map((d) => ({ id: +d[0], emissions: d[1] }))
    .filter((d) => d.emissions != 0)
    .slice(1, 172);

  let data;
  triple_world_map.ISO3 != undefined
    ? (data = merge_trading_triple_data
        .filter((d) => d.iso_code == triple_world_map.ISO3)
        .map((d) => ({
          id: +d.year,
          emissions: +d[indicator]
        })))
    : (data = worlddata);

  return data;
}
```

```js
chart2 = Plot.plot({
  width: 300,
  height: 351,
  marginLeft: 20,
  marginRight: 50,
  marginTop: 60,
  y: {
    grid: true,
    labelOffset: -150,
    label: "↑ CO2 Emisions",
    axis: 'right'
  },
  x: {
    label: 'Year'
  },

  marks: [
    Plot.areaY(chart2data, {
      x: "id",
      y: "emissions",
      fill: accessor.get(indicator).col
    }),
    Plot.dot(chart2data, {
      x: "id",
      y: "emissions",
      r: 10,
      strokeWidth: 3,
      stroke: accessor.get(indicator).col,
      fill: "white",
      filter: (d) => d.id == selected_year_triple_map
    }),
    Plot.text(chart2data, {
      x: "id",
      y: "emissions",
      text: (d) => parseInt(d.emissions),
      dy: -25,
      filter: (d) => d.id == selected_year_triple_map
    }),
    Plot.text(
      [
        triple_world_map.ISO3 != undefined
          ? triple_world_map.ISO3 + " " + 'CO2'
          : "World " + 'CO2'
      ],
      {
        textAnchor: "start",
        frameAnchor: "bottom",
        dy: -5,
        dx: 55,
        fill: "white",
        fontSize: 12
      }
    )
  ]
})
```

#### chart 3

```js
chart3 = Plot.plot({
  width: 1000,
  height: 300,
  marks: [
    Plot.barX(emission_filtered, {
      x: indicator,
      y: "iso_code",
      fill: (d) =>
        d.iso_code == triple_world_map.ISO3
          ? accessor.get(indicator).col2
          : accessor.get(indicator).col,
      sort: { y: "x", reverse: true, limit: 10 }
    })
  ]
})
```
