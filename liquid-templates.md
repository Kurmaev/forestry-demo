---
layout: home
title: liquid-templates
description: Guidlines about various templates
publish_date: 2019-01-31 18:00:00 +0000
date: 2019-02-01 12:53:11 +0000
heading: ''
sub_heading: ''
banner_image: ''
hero_button:
  text: ''
  href: ''
textline: ''
services: []
show_news: false
partners: []
show_staff: false

---
# Templating guidlines

1. All templates written using [Liquid](https://shopify.github.io/liquid/ "Liquid") . You can get some info about it at [https://shopify.github.io/liquid/](https://shopify.github.io/liquid/ "https://shopify.github.io/liquid/") and [https://github.com/Shopify/liquid/wiki/Liquid-for-Designers](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers "https://github.com/Shopify/liquid/wiki/Liquid-for-Designers")
2. Page size is fixed and should have height: 1047px and width: 716px. If your page can be bigger - you need to split it manually via JS/css.
3. Template should have  \`\`\`window.status = 'done';\`\`\`  statement at the end of JS execution. Otherwise your pdf will render 5+ sec
4. You should not remove \`\`\`<style>{{ css }}</style>\`\`\` line - this dropin is used to inserting your css from template into html.
5. You can save even invalid liquid template; but system won't let you enable it until you will fix it.

If you wanna use external resources like images or fonts - you should use Data URI format ([https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs "https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs"))

# Folio Template

### Available variables

**hotel** - _HotelDrop_

**guests** - array of _GuestDrop_

**today** - current date

# Guest Registration form Template

### Available variables

**folio** - _FolioDrop_

**hotel** - _HotelDrop_

**customer** - _CustomerDrop_

**booking** - _BookingDrop_

# Drop reference

### HotelDrop:

    name

    company_name

    company_address

    company_city

    company_country

    company_zip_code

    email

    phone

    show_tax_info

    vat - is vat enabled

    vat_number

    vat_tax_name

    currency_symbol

    invoice_default_notes

    logo_url

    invoice_text

    guest_form_policy

    invoice_logo - logo in base64

    custom_question_first

    custom_question_second

### GuestDrop:

    title

    email

    phone

    company_name

    fax_number

    address

    first_name

    last_name

    country

    city

    state

    nationality

    identification - identification number

    identification_type - identification type name

    zip_code

    type_of_tourism - For Iceland countries only

    addons - container that hold guest's custom fields

### CustomerDrop

    title

    email

    mobile_phone

    company_name

    fax_number

    address

    first_name

    last_name

    country

    city

    state

    nationality

    identification - identification number

    identification_type - identification type name

    visible_name

    is_company - true if customer is company

    is_personal - true if customer is personal

    client_name

    first_name

    last_name

    reference_text

    bill_to

    tax_number

### BookingDrop

    reference

    rooms - array of _BookingRoomDrop_

    checkin_date

    checkout_date

    source

    status

    info

### BookingRoomDrop

    number - room number

    number_of_nights

    number_of_adults

    number_of_children

    checkin_date

    checkout_date

    note

    status - (pending, hold, canceled)

    occupation_status - (pending, checked-in, checked-out)

### FolioDrop:

    status - folio, invoice, receipt, voided

    status_visible - Folio, Invoice, Receipt, Voided Invoice

    visible_number

    folio_rooms: array of _FolioRoomDrop_

    folio_extras: array of _FolioExtraDrop_

    fees_and_city_taxes: array of _TaxDrop_, exclusive fee/city taxes

    inclusive_fees_and_taxes: array of _TaxDrop_, inclusive taxes

    note_override

    note

    verbose_total

    verbose_total_integer_part

    verbose_total_float_part

    tax_date

    date

    total

    total_discount

    subtotal

    charged

    due

### FolioRoomDrop:

    dates: sorted array of _{date: date, price: price}_ objects

    net_with_hidden

    taxes_with_hidden

    amount_with_hidden

    net_per_count

    discounts: array of _FolioRoomDiscount_

### FolioRoomDiscount:

    title

    amount

### FolioExtraDrop

    title

    count

    net

    net_per_count

    aggregated_taxes_total

    amount_after_discount

### TaxDrop

    name

    text_visible

    amounts_sum

    position

    amount

    taxed_amount

    calculation_logic - (percent, fixed, per_person_per_night, per_person_per_booking, per_room_per_night, per_room_per_booking, per_adult_per_booking, per_child_per_booking, per_adult_per_night, per_child_per_night)

    display_calculation_logic

    mode - (tax, city_tax, fee)

    calculation_method - (inclusive, exclusive)

    child_amount