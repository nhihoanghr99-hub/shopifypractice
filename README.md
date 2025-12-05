# shopifypractice
shopifypractice
# /* CSS cho tất cả urgency blocks */
.urgency-block {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px;
  border-radius: 8px;
  margin: 16px 0;
  font-size: 14px;
}

# /* Low Stock Indicator */
.urgency--low-stock {
  background: #fff3cd;
  border-left: 4px solid #ff9800;
}

# /* Limited Time Offer */
.urgency--timer {
  background: #ffebee;
  border-left: 4px solid #f44336;
}

/* High Demand Badge */
.urgency--popular {
  background: #e3f2fd;
  border-left: 4px solid #2196f3;
}

# /* Biểu tượng SVG */
.urgency-block svg {
  width: 20px;
  height: 20px;
  fill: currentColor;
}

----------------------------------------------------------

# Urgency Block:
{% if product.inventory_quantity < 5 %}
  <div class="urgency-block">
    <p>Hurry! Only {{ product.inventory_quantity }} left in stock!</p>
  </div>
{% endif %}

# product.inventory_quantity kiểm tra số lượng sản phẩm còn lại trong kho.
# if condition sẽ hiển thị block urgency khi số lượng sản phẩm còn ít hơn 5.
-------------------------------------------------------------
# Combo Suggestion:
{% if product.tags contains 'combo' %}
  <div class="combo-suggestion">
    <h3>Customers who bought this also bought:</h3>
    <ul>
      {% for related_product in collections.all.products %}
        {% if related_product.tags contains 'combo' %}
          <li>
            <a href="{{ related_product.url }}">{{ related_product.title }}</a>
            <p>{{ related_product.price | money }}</p>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </div>
{% endif %}

# Duyệt qua các sản phẩm trong collections.all.products và kiểm tra xem các sản phẩm có tag 'combo'.
# if condition dùng để chỉ hiển thị sản phẩm liên quan có tag 'combo'.

-------------------------------------------
# “Frequently Bought Together” Block:
<div class="frequently-bought-together">
  <h3>Frequently Bought Together:</h3>
  <ul>
    {% for related_product in collections['related-products'].products %}
      <li>
        <a href="{{ related_product.url }}">{{ related_product.title }}</a>
        <p>{{ related_product.price | money }}</p>
      </li>
    {% endfor %}
  </ul>
</div>

# for loop duyệt qua các sản phẩm trong collection['related-products'].
# Hiển thị các sản phẩm liên quan với giá của chúng.

--------------------------------------------------------
# “Why Customers Love It” Carousel
<div class="why-customers-love-carousel">
  <h3>Why Customers Love It:</h3>
  <div class="carousel">
    {% for review in product.metafields.reviews %}
      <div class="carousel-item">
        <p>{{ review.content }}</p>
        <p>- {{ review.author }}</p>
      </div>
    {% endfor %}
  </div>
</div>

# for loop duyệt qua metafields.reviews để hiển thị nội dung đánh giá.
# Các đánh giá được lấy từ product.metafields.
-------------------------------------------------------------
# Benefit Icons Auto-Render:
<div class="benefit-icons">
  {% for tag in product.tags %}
    {% if tag == 'eco-friendly' %}
      <img src="eco-icon.png" alt="Eco Friendly" />
    {% elsif tag == 'organic' %}
      <img src="organic-icon.png" alt="Organic" />
    {% elsif tag == 'sale' %}
      <img src="sale-icon.png" alt="Sale" />
    {% endif %}
  {% endfor %}
</div>

# for loop duyệt qua các tags của sản phẩm và hiển thị icon tương ứng.
# if condition kiểm tra các tag cụ thể (ví dụ: eco-friendly, organic, sale) và hiển thị biểu tượng tương ứng.
