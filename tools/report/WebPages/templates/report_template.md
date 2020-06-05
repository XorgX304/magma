---
title: {{ report_title }}
---
{% raw %}
{% capture template %}
{% endraw %}
<div class="targets">
    <p>
        Welcome to the magma report. In here you will be able to see the results of the benched fuzzers
        over the target libraries.
        See <a href="https://github.com/HexHive/magma/blob/master/README.md">here</a> for build and run details.
    </p>

    <h2>Benchmark process</h2>
       <p>
           The differents fuzzers are run over the target libraries in which multiple patches have been implemented.
           These patches reintroduce previous corrected bugs. Once the fuzzer campaign is done you will find in this report how much
           bugs where triggered and at what moment. All this gives us enought material to establish a benchmark for the used fuzzers.
        </p>
</div>

<div class="target_description">
    <h2>Targeted Libraries</h2>
    <p>Here are all the currently supported libraries in magma.</p>
    <ul id="target_list">
        {% for (item,num_bugs) in target_list %}
        <li><a href= "libraries/{{item}}.html">{{item}}</a> has a total of {{num_bugs}} implemented bugs</li>
        {% endfor %}
    </ul>
    <p>
        Total number of patches is {{total_bugs}}
    </p>
</div>

<div class="fuzzers">
    <h2>Evaluated Fuzzers</h2>
    <p>Currently magma can evaluate {{fuzzer_list|length}}</p>
    <ul id="fuzzer_list">
        {% for fuzzer in fuzzer_list %}
        <li><a href= "fuzzers/{{fuzzer}}.html">{{fuzzer}}</a></li>
        {% endfor %}
    </ul>
</div>

<div class="general graph">
    <h2>General result</h2>
    <div>
        <img src ="{{plots_dir}}/unique_bug_box.svg">
    </div>
    <div>
        <img src ="{{plots_dir}}/signplot.svg">
    </div>
    <div>
        <img src ="{{plots_dir}}/expected_time_to_bug_heat.svg">
    </div>
</div>
{% raw %}
{% endcapture %}
{{ template | replace: '    ', ''}}
{% endraw %}