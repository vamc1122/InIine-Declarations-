Use Base syntax for greater than or equal to 7.55


lt_data_temp = VALUE #(
  FOR wa IN lt_data
  ( company_code = wa-company_code
    reference    = wa-reference
    customer     = |{ wa-customer ALPHA = IN }|
    " … all other fields explicitly …
  ) ).
