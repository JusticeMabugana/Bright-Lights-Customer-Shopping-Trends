
--checking table content
select * from shoping_trends limit 5;

--checking number of rows
select * from shoping_trends;

--checking duplicate rows
select distinct * from shoping_trends;

--counting number of customers
select count(`customer id`) from shoping_trends;

--age range is 18 and 70
select min(`age`) as min_age,max(`age`) as max_age from shoping_trends;

--age buckets
select age, 
case 
when Age between 18 and 24 then '1. Youth (18-24)'
when Age between 25 and 34 then '2. Young Adults (25-34)'
when Age between 35 and 44 then '3. Adults (35-44)'
when Age between 45 and 55 then '4. Matures (45-54)'
when age is null then '6. Unknown'
else '5. Seniors (55+)'
end as Age_groups
from shoping_trends;

--highest and lowest purchase amount is 100 and 20
select min(purchase_amount) as min_purchase,max(purchase_amount) as max_purchase from shoping_trends;

--purchase amount buckets
select purchase_amount, 
case 
when purchase_amount between 20 and 40 then '1. Low (20-40)'
when purchase_amount between 41 and 60 then '2. Medium (41-60)'
when purchase_amount between 61 and 80 then '3. High (61-80)'
when purchase_amount is null then '5. Unknown'
else '4. Very High (81+)'
end as purchase_amount_groups
from shoping_trends;

--highest and lowest rating is 5 and 2.5
select min(`review rating`) as min_rating,max(`review rating`) as max_rating from shoping_trends;

--rating buckets
select `review rating`, 
case 
when `review rating` between 2.5 and 3.4 then '1. Poor (2.5 to 3.4)'
when `review rating` between 3.5 and 4.4 then '2. Average (3.5 to 4.4)'
when `review rating` between 4.5 and 4.8 then '3. Good (4.5 to 5)'
when `review rating` is null then '5. Unknown'
else '4. Excellent (5+)'
end as rating_groups
from shoping_trends;

--highest and lowest previous purchases is 1 and 50
select min(`previous purchases`) as min_purchases,max(`previous purchases`) as max_purchases from shoping_trends;

--previous purchases buckets
select `previous purchases`, 
case 
when `previous purchases` between 1 and 5 then '1. Low (1-5)'
when `previous purchases` between 6 and 10 then '2. Medium (6-10)'
when `previous purchases` between 11 and 20 then '3. High (11-20)'
when `previous purchases` is null then '5. Unknown'
else '4. Very High (21+)'
end as previous_purchases_groups
from shoping_trends;

--Nulls
select coalesce(`item purchased`, 'Unkown')
from shoping_trends;

--final code
Select coalesce(Gender, 'Unknown') as Gender,
       coalesce(`item purchased`, 'Unkown') as Items_Purchased,
       coalesce(Category, 'Unkown') as Category,
       coalesce(Location, 'Unknown') as Location,
       coalesce(Size, 'Unknown') as Size,
       coalesce(Color, 'Unknown') Colour,
       coalesce(`season`, 'Unknown') as Season,
       coalesce(`Subscription Status`, 'Unknown') as Subscription_Status,
       coalesce(`shipping type`, 'Unknown') as Shipping_Type,
       coalesce(`discount applied`, 'Unknown') as Discount_Applied,
       coalesce(`promo code used`, 'Unknown') as Promo_Code_Used,
       coalesce(`payment method`, 'Unknown') as Payment_Method,
       coalesce(`frequency of purchases`, 'Unknown') as Frequency_of_Purchases,
  case 
when Age between 18 and 24 then '1. Youth (18-24)'
when Age between 25 and 34 then '2. Young Adults (25-34)'
when Age between 35 and 44 then '3. Adults (35-44)'
when Age between 45 and 55 then '4. Matures (45-54)'
when age is null then '6. Unknown'
else '5. Seniors (55+)'
end as Age_groups,
case 
when purchase_amount between 20 and 40 then '1. Low (20-40)'
when purchase_amount between 41 and 60 then '2. Medium (41-60)'
when purchase_amount between 61 and 80 then '3. High (61-80)'
when purchase_amount is null then '5. Unknown'
else '4. Very High (81+)'
end as purchase_amount_groups,
case 
when `review rating` between 2.5 and 3.4 then '1. Poor (2.5 to 3.4)'
when `review rating` between 3.5 and 4.4 then '2. Average (3.5 to 4.4)'
when `review rating` between 4.5 and 4.8 then '3. Good (4.5 to 5)'
when `review rating` is null then '5. Unknown'
else '4. Excellent (5+)'
end as rating_groups,
case 
when `previous purchases` between 1 and 5 then '1. Low (1-5)'
when `previous purchases` between 6 and 10 then '2. Medium (6-10)'
when `previous purchases` between 11 and 20 then '3. High (11-20)'
when `previous purchases` is null then '5. Unknown'
else '4. Very High (21+)'
end as previous_purchases_groups
from shoping_trends;
