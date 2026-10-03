# JBB Custom

Client-specific customisations for Jai Balaji Billiards only. Intentionally empty (skeleton only); it exists so JBB-only changes never go into product apps.

## Dependencies

- `erpnext`
- `quoteshop`

## Install order

Install apps on a site in exactly this order:

```
erpnext -> hrms -> crm -> frappe_whatsapp -> erp_custom -> quoteshop -> hrms_custom -> jbb_custom
```

```bash
bench --site <site> install-app jbb_custom
```

## Modules

- JBB Custom (`jbb_custom/jbb_custom/`)

Customisations on standard DocTypes (custom fields, property setters) are versioned as
`<module>/custom/<doctype>.json` via **Customize Form -> Actions -> Export Customizations**
(or `bench --site <site> export-customizations`) — not fixtures.

## Rules

- Never edit standard apps (frappe, erpnext, hrms, crm, frappe_whatsapp).
- One owner per custom field / hook: never define the same field in two apps.
- No circular dependencies (e.g. `erp_custom` never depends on `quoteshop`).
- Client-specific changes only go in client apps (e.g. `jbb_custom`).
- Business data (brand, products, settings) is entered on the site, not hard-coded.

## License

MIT
