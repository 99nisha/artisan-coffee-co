# Specialty Coffee Roastery & Café - Complete Data Schema

## 1. Customer Management

### customers
- customer_id (Primary Key)
- first_name
- last_name
- email
- phone_number
- date_of_birth
- registration_date
- preferred_contact_method
- loyalty_points_balance
- total_lifetime_spend
- average_order_value
- visit_frequency
- last_visit_date
- customer_status (active, inactive, vip)
- marketing_opt_in
- dietary_restrictions
- favorite_drinks
- preferred_pickup_time
- notes

### customer_addresses
- address_id (Primary Key)
- customer_id (Foreign Key)
- address_type (billing, shipping, primary)
- street_address
- city
- state_province
- postal_code
- country
- is_default

## 2. Product Catalog

### coffee_beans
- bean_id (Primary Key)
- origin_country
- origin_region
- farm_name
- farmer_name
- bean_variety
- processing_method
- altitude_grown
- harvest_date
- cupping_score
- flavor_notes
- certification (organic, fair_trade, rainforest_alliance)
- cost_per_pound
- supplier_id
- quality_grade
- moisture_content
- density

### roast_profiles
- profile_id (Primary Key)
- bean_id (Foreign Key)
- roast_level (light, medium, dark)
- roast_temperature_curve
- roast_duration_minutes
- development_time_ratio
- first_crack_time
- end_temperature
- color_measurement
- created_by_roaster
- creation_date
- cupping_notes
- recommended_brewing_methods

### products
- product_id (Primary Key)
- product_name
- product_type (coffee_bag, beverage, food, merchandise)
- bean_id (Foreign Key, if applicable)
- roast_profile_id (Foreign Key, if applicable)
- description
- size_weight
- unit_cost
- selling_price
- profit_margin
- category
- is_seasonal
- allergen_information
- nutritional_info
- barcode_sku
- supplier_id
- minimum_stock_level
- maximum_stock_level
- shelf_life_days
- storage_requirements

## 3. Inventory Management

### inventory
- inventory_id (Primary Key)
- product_id (Foreign Key)
- current_stock_quantity
- reserved_quantity
- available_quantity
- last_updated
- location (warehouse, display, storage)
- expiration_date
- batch_number
- cost_basis

### inventory_transactions
- transaction_id (Primary Key)
- product_id (Foreign Key)
- transaction_type (purchase, sale, adjustment, waste, transfer)
- quantity_change
- transaction_date
- reference_number
- notes
- performed_by_employee_id
- cost_impact

### suppliers
- supplier_id (Primary Key)
- supplier_name
- contact_person
- email
- phone
- address
- payment_terms
- lead_time_days
- minimum_order_quantity
- supplier_type (green_beans, food, equipment, packaging)
- quality_rating
- reliability_score
- certifications

## 4. Sales & Orders

### orders
- order_id (Primary Key)
- customer_id (Foreign Key)
- order_date
- order_time
- order_type (in_store, online, wholesale)
- payment_method
- payment_status
- order_status (pending, preparing, ready, completed, cancelled)
- subtotal
- tax_amount
- tip_amount
- discount_amount
- total_amount
- pickup_delivery_time
- special_instructions
- employee_id (who took the order)

### order_items
- order_item_id (Primary Key)
- order_id (Foreign Key)
- product_id (Foreign Key)
- quantity
- unit_price
- total_price
- customizations
- preparation_notes

### daily_sales_summary
- date
- total_revenue
- total_orders
- average_order_value
- customer_count
- new_customers
- returning_customers
- peak_hour
- weather_condition
- special_events

## 5. Production & Roasting

### roasting_batches
- batch_id (Primary Key)
- bean_id (Foreign Key)
- roast_profile_id (Foreign Key)
- roast_date
- green_bean_weight_in
- roasted_bean_weight_out
- yield_percentage
- roaster_employee_id
- roast_quality_score
- batch_notes
- environmental_temp
- environmental_humidity
- roaster_machine_id

### quality_control
- qc_id (Primary Key)
- batch_id (Foreign Key)
- cupping_date
- cupper_employee_id
- aroma_score
- flavor_score
- aftertaste_score
- acidity_score
- body_score
- balance_score
- overall_score
- defects_noted
- approved_for_sale
- notes

## 6. Equipment & Maintenance

### equipment
- equipment_id (Primary Key)
- equipment_name
- equipment_type (roaster, espresso_machine, grinder, etc.)
- manufacturer
- model_number
- serial_number
- purchase_date
- warranty_expiration
- location
- status (operational, maintenance, retired)
- last_maintenance_date
- next_maintenance_due

### maintenance_logs
- maintenance_id (Primary Key)
- equipment_id (Foreign Key)
- maintenance_date
- maintenance_type (routine, repair, calibration)
- performed_by
- description
- parts_replaced
- cost
- next_maintenance_date

## 7. Staff Management

### employees
- employee_id (Primary Key)
- first_name
- last_name
- email
- phone
- hire_date
- position (barista, roaster, manager, owner)
- hourly_wage
- employment_status (active, inactive, terminated)
- certifications (barista, roasting, food_safety)
- emergency_contact_name
- emergency_contact_phone
- availability_schedule

### employee_schedules
- schedule_id (Primary Key)
- employee_id (Foreign Key)
- date
- start_time
- end_time
- position_assigned
- actual_clock_in
- actual_clock_out
- break_duration
- overtime_hours

### training_records
- training_id (Primary Key)
- employee_id (Foreign Key)
- training_type
- completion_date
- instructor
- certification_earned
- expiration_date
- score_achieved

## 8. Financial Management

### expenses
- expense_id (Primary Key)
- expense_date
- category (rent, utilities, supplies, marketing, equipment, labor)
- vendor_name
- description
- amount
- payment_method
- receipt_number
- is_recurring
- tax_deductible

### revenue_streams
- revenue_id (Primary Key)
- date
- stream_type (retail_sales, wholesale, catering, online, classes)
- amount
- associated_order_id
- payment_method
- processing_fees

### tax_records
- tax_record_id (Primary Key)
- tax_period
- gross_revenue
- total_expenses
- taxable_income
- sales_tax_collected
- sales_tax_paid
- payroll_taxes
- business_license_fees

## 9. Marketing & Events

### marketing_campaigns
- campaign_id (Primary Key)
- campaign_name
- campaign_type (email, social_media, print, event)
- start_date
- end_date
- budget
- target_audience
- success_metrics
- actual_reach
- conversion_rate
- roi

### events
- event_id (Primary Key)
- event_name
- event_type (cupping, class, private_party, pop_up)
- event_date
- start_time
- end_time
- capacity
- tickets_sold
- revenue
- expenses
- instructor_employee_id
- notes

### loyalty_program
- transaction_id (Primary Key)
- customer_id (Foreign Key)
- transaction_date
- points_earned
- points_redeemed
- point_balance_change
- related_order_id
- expiration_date

## 10. Operational Analytics

### daily_operations
- date
- opening_time
- closing_time
- staff_count
- customer_count
- weather
- local_events
- equipment_issues
- waste_amount
- energy_consumption

### seasonal_trends
- period (month/quarter)
- product_category
- sales_volume
- revenue
- customer_preference_shifts
- inventory_turnover
- profit_margins

## 11. Compliance & Certifications

### food_safety_logs
- log_id (Primary Key)
- date
- temperature_readings
- cleaning_schedule_completed
- employee_hygiene_checklist
- equipment_sanitization
- compliance_officer
- violations_noted
- corrective_actions

### certifications
- certification_id (Primary Key)
- certification_type (organic, fair_trade, food_handler, business_license)
- issuing_authority
- certificate_number
- issue_date
- expiration_date
- renewal_required
- compliance_status

## Key Business Intelligence Metrics to Track

### Customer Metrics
- Customer Acquisition Cost (CAC)
- Customer Lifetime Value (CLV)
- Customer Retention Rate
- Net Promoter Score (NPS)
- Average Order Value (AOV)
- Purchase Frequency

### Operational Metrics
- Inventory Turnover Rate
- Waste Percentage
- Labor Cost Percentage
- Equipment Utilization
- Order Fulfillment Time
- Quality Control Pass Rate

### Financial Metrics
- Gross Profit Margin by Product
- Monthly Recurring Revenue
- Seasonal Revenue Patterns
- Cost of Goods Sold (COGS)
- Break-even Point
- Cash Flow Analysis

### Marketing Metrics
- Marketing ROI by Channel
- Social Media Engagement
- Email Open/Click Rates
- Event Attendance Rates
- Referral Rates

## Data Relationships & Constraints

### Primary Relationships
- customers → orders (one-to-many)
- orders → order_items (one-to-many)
- products → inventory (one-to-one)
- coffee_beans → roast_profiles (one-to-many)
- roast_profiles → products (one-to-many)
- employees → orders (many-to-one for order taker)
- suppliers → products (many-to-many via supplier product catalog)

### Business Rules to Enforce
- Inventory cannot go negative
- Roast batches must have quality control before sale approval
- Employee schedules cannot overlap for same person
- Loyalty points have expiration dates
- Equipment maintenance schedules are mandatory
- Financial transactions must balance
- Food safety logs are required daily
- Customer data privacy compliance (GDPR/CCPA)

This schema provides a comprehensive foundation for understanding all the data touchpoints, operational considerations, and business intelligence needs of a specialty coffee roastery and café business.