# Deathrates for Suicide by Demographic

<p> <b>Author:</b> Candace Cox</p>
<p> <b>Analyst:</b> Candace Cox</p>
<p> <b>Date:</b> May 15, 2024</p>
<p> <b>Data Source:</b> Kaggle free datasets
https://www.kaggle.com/datasets/varundeepakgudhe/u-s-suicide-rates-by-sex-race-age-origin</p>
<p><b>Purpose:</b> The purpose of this document is to outline the analysis steps taken and the conclusion of the analysis.
The specific goals of the analysis will be outlined in the "questions" section of the document below.


<h2>Data Catalogue</h2>
<table>
    <tr>
        <th>Original Field Name</th>
        <th>Updated Field Name(s)</th>
        <th>Data Type</th>
        <th>Field Description</th>
    </tr>
    <tr>
        <td>INDICATOR</td>
        <td></td>
        <td>varchar</td>
        <td>Value: "Death rates for suicide".
            <p>No other values in column.</p>
        </td>
    </tr>
    <tr>
        <td>UNIT</td>
        <td></td>
        <td>varchar</td>
        <td>Unit of measurement for the indicator.
            <p>Two Values:</p>
            <p>"Deaths per 100,000 resident population, age-adjusted"</p>
            <p>"Deaths per 100,000 resident population, crude"</p>
        </td>
    </tr>
    <tr>
        <td>STUB_NAME</td>
        <td></td>
        <td>varchar</td>
        <td>This is a broad descriptor of the combination of values that the STUB_NAME_NUM and STUB_LABEL_NUM values represent. This is a combination of one or more of the following:
            <p>- sex</p>
            <p>- age</p>
            <p>- race</p>
            <p>- hispanic origin</p>
            <p>- single race</p>
        </td>
    </tr>
    <tr>
        <td>STUB_NAME_NUM</td>
        <td></td>
        <td>int</td>
        <td>This is a count of the combination of descriptors from STUB_NAME.</td>
    </tr>
    <tr>
        <td>STUB_LABEL</td>
        <td></td>
        <td>varchar</td>
        <td>This is the specific demographic information indicated by the STUB_NAME. 
            <p>Example: "sex" in the STUB_NAME would be "male" or "female" in the STUB_LABEL.</p>
        </td>
    </tr>
    <tr>
        <td>STUB_LABEL_NUM</td>
        <td></td>
        <td>int</td>
        <td>A count for the combination of specific descriptors in the STUB_LABEL.</td>
    </tr>
    <tr>
        <td>YEAR</td>
        <td></td>
        <td>int</td>
        <td>The year that the suicide happened. 
            <p>Values: 1950, 1960, 1970, 1980-2018 inclusive.</p>
        </td>
    </tr>
    <tr>
        <td>YEAR_NUM</td>
        <td></td>
        <td>int</td>
        <td>Indices of the YEAR column.</td>
    </tr>
    <tr>
        <td>AGE</td>
        <td></td>
        <td>varchar</td>
        <td>Age of suicide as a range.</td>
    </tr>
    <tr>
        <td>AGE_NUM</td>
        <td></td>
        <td>float</td>
        <td>Seems to be an index column for the AGE groups. The whole part of the float indicates a full age range and the decimals represent subsets of the original range.
            <p>Example: </p>
            <p>2.0 represents ages 15-24</p>
            <p>2.1 represents ages 15-19 (the lower half of the original range)</p>
            <p>2.2 represent ages 20-24 (the upper half of the original range)</p>
        </td>
    </tr>
    <tr>
        <td>ESTIMATE</td>
        <td></td>
        <td>float</td>
        <td>UNKNOWN</td>
    </tr>
    <tr>
        <td>FLAG</td>
        <td></td>
        <td></td>
        <td>UNKNOWN, Value: NULL, *</td>
    </tr>
</table>

<h2>Data Cleansing Steps</h2>
<ol>
  <li>Drop fields: ESTIMATE, FLAG </li>
    <ol>
      <li>It is not clear what these field represent, and are not needed for analysis.</li>
    </ol>
  <li>Change field names to be non-capital snake case.</li>
  <li>Cast each field to specific data type to ensure consistency.</li>
  <li>Break out STUB_NAME and STUB_LABEL into multiple columns for sex, ethnicity, etc. The STUB_NAME will be the field name and the STUB_LABEL will be the value.</li>
    <ol>
      <li>This will allow for more thorough analysis of specific genders and ethnicities.</li>
    </ol>
</ol>

<h2>Questions to be Answered</h2>
