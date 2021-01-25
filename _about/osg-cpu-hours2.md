---
layout: default
---

## The Open Science Grid

<br/>
<hr/>
<br/>

<style>
.osg_hours td,th.ar { text-align: right }
.osg_table_footer {
    font-weight: bold;
    font-style: italic;
    text-align: center;
    margin-top: 1em
}
.c75 {
    margin: auto;
    max-width: 75%
}
.h2ts {
    float: right;
    font-size: small;
}

.xtooltip {
  position: relative;
}

.xtooltip .xtooltiptext {
  visibility: hidden;
  background-color: #555;
  color: #fff;
  text-align: left;
  white-space: nowrap;
  font-size: small;
  border-radius: 6px;
  padding: 5px 5px;
  position: absolute;
  z-index: 1;
  bottom: 125%;
  left: 50%;
  margin-left: -50%;
  opacity: 0;
  transition: opacity 0.3s;
}

.xtooltip:hover .xtooltiptext {
  visibility: visible;
  opacity: 1;
}
</style>

<div>
<div class="c75">

<h2 id="osg_cpu_hours_h2">OSG CPU Hours</h2>
<table class="osg_hours">

<tr>
  <th class="ar"></th>
  <th class="ar">Last 24 Hours</th>
  <th class="ar">Last 30 Days</th>
  <th class="ar">Last 12 Months</th>
</tr>

<tr id="cc_star_usage_row">
  <th>All CC&#42;</th>
</tr>

<tr id="cc_star_count_row">
  <th># CEs Reporting</th>
</tr>

<tr id="amnh_usage_row">
  <th>AMNH CC&#42;</th>
</tr>

<tr id="amnh_count_row">
  <th># CEs Reporting</th>
</tr>

<tr id="all_non_lhc_row">
  <th>All Science, excluding LHC</th>
</tr>

<tr id="gpu_usage_row">
  <th>GPU Utilization</th>
</tr>

<tr id="cc_star_gpu_usage_row">
  <th>CC&#42; GPU Utilization</th>
</tr>

<tr id="cc_star_gpu_count_row">
  <th># CEs Reporting</th>
</tr>

</table>
<p class="osg_table_footer">
All Science except LHC Experiments
</p>

</div>
</div>
<br/>

<script>
(function() {
  $.getJSON("https://path-cc.io/metrics/osg-cpu-hours.json")
    .done(function(data) {
      $.each(data.amnh_usage, function(i, x) {
        $('<td>' + x + "</td>").appendTo("#amnh_usage_row");
      });
      $.each(data.amnh_count, function(i, x) {
        $('<td class="xtooltip">' + x
          +   '<span class="xtooltiptext">'
          +     data.amnh_fqdns[i].join("<br/>")
          +   '</span>'
          + "</td>").appendTo("#amnh_count_row");
      });
      $.each(data.cc_star_usage, function(i, x) {
        $('<td>' + x + "</td>").appendTo("#cc_star_usage_row");
      });
      $.each(data.cc_star_count, function(i, x) {
        $('<td class="xtooltip">' + x
          +   '<span class="xtooltiptext">'
          +     data.cc_star_fqdns[i].join("<br/>")
          +   '</span>'
          + "</td>").appendTo("#cc_star_count_row");
      });
      $.each(data.all_non_lhc, function(i, x) {
        $('<td>' + x + "</td>").appendTo("#all_non_lhc_row");
      });
      $.each(data.gpu_usage, function(i, x) {
        $('<td>' + x + "</td>").appendTo("#gpu_usage_row");
      });
      $.each(data.cc_star_gpu_usage, function(i, x) {
        $('<td>' + x + "</td>").appendTo("#cc_star_gpu_usage_row");
      });
      $.each(data.cc_star_gpu_count, function(i, x) {
        $('<td class="xtooltip">' + x
          +   '<span class="xtooltiptext">'
          +     data.cc_star_gpu_fqdns[i].join("<br/>")
          +   '</span>'
          + "</td>").appendTo("#cc_star_gpu_count_row");
      });
      $('<span class="h2ts"> as of ' + data.last_update_str + "</span>").appendTo("#osg_cpu_hours_h2");
    });
})();
</script>

