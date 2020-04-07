---
title: Introduction
redirect_from: /about/index.html
---

### What We Do

The Open Science Grid (OSG) provides common service and support for resource providers and scientific institutions using
a distributed fabric of high throughput computational services.  The OSG does not own resources but provides software
and services to users and resource providers alike to enable the opportunistic usage and sharing of resources.  The OSG
is funded through a diverse portfolio of awards from the National Science Foundation and the Department of
Energy.

The OSG supports science such as:

- High Energy Physics
- Structural Biology
- Community VO (multiple sciences): OSG Connect

The OSG is primarily used as a high-throughput grid where scientific problems are solved by breaking them down into a
very large number of individual jobs that can run independently.  The most successful opportunistic applications run on
the OSG share the following characteristics:

- The application is a Linux application for the x86 or x86_64 architecture.
- The application is single- or multi-threaded but does not require message passing.
- The application has a small runtime between 1 and 24 hours.
- The application can handle being unexpectedly killed and restarted.
- The application is built from software that does not require contact to licensing servers.
- The scientific problem can be described as a workflow consisting of jobs of such kind.
- The scientific problem requires running a very large number of small jobs rather than a few large jobs.

### More About OSG

- Please see the [system administrator docs](https://opensciencegrid.org/docs/) for more information regarding the OSG.
- [Grid Accounting portal](https://gracc.opensciencegrid.org/)

<br/>
<hr/>
<br/>

<div>

<h2>OSG CPU Hours</h2>
<table>

<tr>
  <th></th>
  <th>Last 24 Hours</th>
  <th>Last 30 Days</th>
  <th>Last 12 Months</th>
</tr>

<tr id="all_non_lhc_row">
  <th>All Science, excluding LHC</th>
</tr>

<tr id="gpu_usage_row">
  <th>GPU Utilization</th>
</tr>

</table>
<p style="font-weight: bold; font-style: italic; text-align: center; margin-top: 1em">
All Science except LHC Experiments
</p>

</div>

<script>
(function() {
  $.getJSON("https://web0000.chtc.wisc.edu/osg-cpu-hours.json")
    .done(function(data) {
      $.each(data.all_non_lhc, function(i, x) {
        $("<td>" + x + "</td>").appendTo("#all_non_lhc_row");
      });
      $.each(data.gpu_usage, function(i, x) {
        $("<td>" + x + "</td>").appendTo("#gpu_usage_row");
      });
    });
})();
</script>

