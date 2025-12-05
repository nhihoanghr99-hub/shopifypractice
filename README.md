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
