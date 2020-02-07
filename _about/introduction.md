---
title: Introduction
redirect_from: /about/index.html
---

### What We Do

The Open Science Grid (OSG) provides common service and support for resource providers and scientific institutions using
a distributed fabric of high throughput computational services.  The OSG does not own resources but provides software
and services to users and resource providers alike to enable the opportunistic usage and sharing of resources.  The OSG
is funded through a diverse portfolio of awards from the National Science Foundation and the Department of
Energy.  [Click here](/assets/pdf/OSG_Calling_Card_110515.pdf) for a two-page printable overview of OSG.

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

<hr/>

<div>
<h2>OSG CPU Hours for CC*</h2>
<table>
<tr>
<th></th>
<th>Last 30 Days</th>
<th>Last 90 Days</th>
<th>Last 365 Days</th>
</tr>
<tr id="osg_hours_row">
<th>CPU Hours</th>
</tr>
<tr id="fqdn_count_row">
<th>CEs Reporting</th>
</tr>
</table>
<br/><br/>
<h2>OSG GPU Hours for CC*</h2>
<table>
<tr>
<th></th>
<th>Last 30 Days</th>
<th>Last 90 Days</th>
<th>Last 365 Days</th>
</tr>
<tr id="osg_hours_gpus_row">
<th>GPU Hours</th>
</tr>
<tr id="fqdn_count_gpus_row">
<th>CEs Reporting</th>
</tr>
</table>
<br/><br/>
<p id="last_update">Last updated: </p>
</div>

<script src="https://code.jquery.com/jquery-3.4.1.js">
</script>
<script>
(function() {
  $.getJSON("https://web0000.chtc.wisc.edu/osg-cpu-hours.json")
    .done(function(data) {
      $.each(data.hours_all, function(i, x) {
        $("<td>" + x + "</td>").appendTo("#osg_hours_row");
      });
      $.each(data.fqdn_counts_all, function(i, x) {
        $("<td>" + x + "</td>").appendTo("#fqdn_count_row");
      });
      // GPU jobs
      $.each(data.hours_gpu, function(i, x) {
        $("<td>" + x + "</td>").appendTo("#osg_hours_gpus_row");
      });
      $.each(data.fqdn_counts_gpu, function(i, x) {
        $("<td>" + x + "</td>").appendTo("#fqdn_count_gpus_row");
      });
      $("<span>" + data.last_update + "</span>").appendTo("#last_update");
    });
})();
</script>

