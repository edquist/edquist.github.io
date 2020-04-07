---
layout: default
---

{% include homepage_top.html %}

## The Open Science Grid

A national, distributed computing partnership for data-intensive research

<div id="osg-special-banner">
  <p class="special-banner-1"><strong>Extra OSG Support for COVID-19 Research</strong></p>
  <p class="special-banner-1" style="margin-bottom: 0.5ex;">
    We are here to help you with your COVID-19 research! Please contact us at
    <a href="mailto:help@opensciencegrid.org">help@opensciencegrid.org</a> if
    you or your organization:
  </p>
  <ul>
    <li>Have computing and/or data needs for research relevant to the COVID-19 pandemic;</li>
    <li>
      Already share &ndash; or want to share &ndash; research computing capacity at your local organization via OSG,
      and want to prioritize COVID-19 research; or
    </li>
    <li>Have any other creative ideas for how OSG can contribute &ndash; we are all ears!</li>
  </ul>
</div>
<div class="row">
  <div class="col-lg-4">
    <h3>What We Do</h3>
    <p>The OSG facilitates access to distributed high throughput computing for research in the US.
    The resources accessible through the OSG are contributed by the community, organized by the OSG, and governed by the OSG consortium.
    In the last 12 months, we have provided more than 1.2 billion CPU hours to researchers across a wide variety of projects.
    </p>
  </div>
  <div class="col-lg-4">
    <h3>Submit Locally, Run Globally</h3>
    <p>Researchers can submit batch jobs from their home institution - or OSG-provided submit points - in order to access their local resources and expand
    elastically out to the OSG, leverage the distributed nature of our consortium.</p>
  </div>
  <div class="col-lg-4">
    <h3>Sharing Is Key</h3>
    <p><em>Sharing is a core principle of the OSG.</em>  Over 100 million CPU hours delivered on the OSG in the past year were opportunistic: they would have remained on but idle
if it wasn't for the OSG. Sharing allows individual researchers to access larger computing resources and large organizations to keep their utilization high.</p>
  </div>
</div>
<div class="row">
  <div class="col-lg-4">
    <h3>Resource Providers</h3>
    <p>The Open Science Grid consists of computing and storage elements at over 100 individual sites spanning the United States.
    These sites, primarily at universities and national labs, range in size from a few hundred to tens of thousands of CPU cores.</p>
  </div>
  <div class="col-lg-4">
    <h3>The OSG Software Stack</h3>
    <p>The OSG provides an integrated software stack to enable high throughput computing; <a href="docs/">visit our technical documents website for information</a>.</p>
  </div>
  <div class="col-lg-4">
    <h3>Find Us!</h3>
    <p>Are you a user wanting more computing resources?</p>
    <p>Are you a resource provider wanting to join our collaboration?</p>
    <p>If so, find us at the <a href="https://support.opensciencegrid.org">support desk</a>.</p>
    <p>To see the breadth of the OSG use, <a href="https://gracc.opensciencegrid.org">explore our accounting portal</a>.</p>
  </div>
</div>

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
</style>

<div>
<div class="c75">

<h2>OSG CPU Hours</h2>
<table class="osg_hours">

<tr>
  <th class="ar"></th>
  <th class="ar">Last 24 Hours</th>
  <th class="ar">Last 30 Days</th>
  <th class="ar">Last 12 Months</th>
</tr>

<tr id="amnh_usage_row">
  <th>AMNH</th>
</tr>

<tr id="all_non_lhc_row">
  <th>All Science, excluding LHC</th>
</tr>

<tr id="gpu_usage_row">
  <th>GPU Utilization</th>
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
  $.getJSON("https://web0000.chtc.wisc.edu/osg-cpu-hours.json")
    .done(function(data) {
      $.each(data.amnh_usage, function(i, x) {
        $('<td>' + x + "</td>").appendTo("#amnh_usage_row");
      });
      $.each(data.all_non_lhc, function(i, x) {
        $('<td>' + x + "</td>").appendTo("#all_non_lhc_row");
      });
      $.each(data.gpu_usage, function(i, x) {
        $('<td>' + x + "</td>").appendTo("#gpu_usage_row");
      });
    });
})();
</script>

