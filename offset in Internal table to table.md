SnipSave
Dashboard
SnipSave CLI
Search Snippets
Search Snippets
Logout
SnipSave is shutting down on August 31, 2026. Learn more


vamsi mudunuri vamsimudunuri
View user profile
Show Line Numbers
Wrap Text
offset for select query
ABAP
Copy
test case 1.
TYPES: BEGIN OF ty_gen,
         idnt1 TYPE zxx_generic_data-idnt1,
         idnt2 TYPE zxx_generic_data-idnt2,
         idnt3 TYPE zxx_generic_data-idnt3,
         seqno TYPE zxx_generic_data-seqno,
         flval TYPE zxx_generic_data-flval,
       END OF ty_gen.

DATA : it_gen1 TYPE TABLE OF ty_gen,
       wa_gen1 TYPE ty_gen.
DATA : it_gen TYPE TABLE OF ty_gen,
       wa_gen TYPE ty_gen.
  
        it_gen1 = VALUE #( FOR field1 IN ti_drseg ( idnt2(char30) = field1-werks idnt3(char30) = field1-matnr ) ) .

         select idnt1,
                idnt2,
                idnt3,
                seqno,
                flval
            FROM zxx_generic_data INTO TABLE @it_gen FOR ALL ENTRIES IN @it_gen1 WHERE IDNT2(char30) = @it_gen1-idnt2(char30) AND IDNT3 =  @it_gen1-idnt3(char30).



test case 2.

  BEGIN OF lty_bseg_temp,
    lv_object_id TYPE cdpos-objectid,
    lv_belnr     TYPE bseg-belnr,
    lv_gjahr     TYPE bseg-gjahr,
  END OF lty_bseg_temp,

        SELECT bukrs,              "Company Code
               belnr,              "Document Number
               bldat,              "Document Date
               usnam,              "User Name
               kursf,              "Exchange rate
               xblnr               "Reference
          FROM bkpf                                "#EC CI_NO_TRANSFORM
          INTO TABLE @lt_bkpf
          FOR ALL ENTRIES IN @lt_bseg1
          WHERE belnr = @lt_bseg1-belnr
          AND bldat = @lt_bseg1-h_bldat
          AND bukrs = @lt_bseg1-bukrs.


        CLEAR : lt_bseg_temp.
        lt_bseg_temp = VALUE #( FOR field1 IN lt_bseg1 (
                                                    lv_belnr = field1-awkey+0(10) lv_gjahr =  field1-awkey+10(4) ) ) .

X
GitHub
YouTube
Discord
LinkedIn
© 2026 Wavex LLC. All rights reserved.

vamsimudunuri's Dashboard | SnipSave
