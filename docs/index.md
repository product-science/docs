<style>
.md-sidebar {
    display: none;
}
.md-main {
    margin-left: auto;
}

/* Styles for mobile screens */
@media (max-width: 768px) {
  .products-container {
    display: block;
  }
  .product {
    padding: 20px;
  }
}

/* Styles for desktop screens */
@media (min-width: 769px) {
  .products-container {
    display: flex;
  }
  .product {
    flex: 1;
    padding: 30px 100px;
  }
}

</style>

# Product Science Documentation

[Product Science](https://www.productscience.ai/)
develops tools that enhance software performance and efficiency
by uncovering and addressing inefficiencies at the code level.
We analyze the code and
actual runtime data to pinpoint performance issues. Our AI enables us
to do it more efficiently by providing unique insights for data
visualizations to help developers identify the problem
right away.

## Explore documentation for our products

<div class="products-container">
  <div class="product">
    <a href="cloud/overview">
        <img src="/images/Cloud.png" alt="Image Description 1" style="width:100%;">
        <p style="text-align: center; font-weight: bold;">CodeTuner for Cloud</p>
    </a>
  </div>
  <div class="product">
    <a href="mobile/overview">
        <img src="/images/Mobile.png" alt="Image Description 2" style="width:100%;">
        <p style="text-align: center; font-weight: bold;">CodeTuner for Mobile</p>
    </a>
  </div>
  <div class="product">
    <a href="ra/overview">
        <img src="/images/Regression.png" alt="Image Description 3" style="width:100%;">
        <p style="text-align: center; font-weight: bold;">Regression Analysis for Mobile</p>
    </a>
  </div>
</div>
