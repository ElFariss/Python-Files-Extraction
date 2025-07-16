# ETL Pipeline for Mixed-Format Data

This repository contains a modified version of the ETL pipeline from IBM’s Data Engineering labs. The code is adapted to work in a Jupyter Notebook environment and is tailored for scenarios where data is sourced from **three different file types**: CSV, JSON, and XML.

The pipeline extracts data from each format, applies a simple transformation, and consolidates the results into a single CSV file.

---

## Purpose

This ETL script is designed for demonstration or educational use where you are working with:

- `CSV` files (tabular format)
- `JSON` files (line-delimited)
- `XML` files (with a known structure)

It assumes that **all three formats represent the same kind of data** (e.g., car listings) but may come from different systems or exports.

---

## Structure

- **Extract**: Reads all `.csv`, `.json`, and `.xml` files in the current directory (excluding the output file).
- **Transform**: Rounds numeric values (like price) and ensures type consistency.
- **Load**: Writes the combined, cleaned data to a single CSV.
- **Log**: Appends ETL progress messages to a log file with timestamps.

---

## Limitations

- The code is hardcoded to expect certain fields:  
  `car_model`, `year_of_manufacture`, `price`, and `fuel`.
  
- XML parsing depends on these tags existing in each `<record>` element.

- The schema for XML must be manually defined in `dtype_map` (you can preview XML fields using the `get_xml_headers()` helper function).

This means the pipeline is **not fully general-purpose** — it's suitable for controlled data ingestion workflows or learning environments where input formats are known.

---

## Usage (Jupyter Notebook)

1. Place your `.csv`, `.json`, and `.xml` files in the same directory.
2. Run the notebook cells step-by-step:
    - Load the helper functions
    - Use `get_xml_headers("example.xml")` to verify XML structure
    - Modify the `dtype_map` in `extract_from_xml()` if needed
    - Run the ETL steps
3. The final output will be saved to `transformed_data.csv`.

---

## Example XML

```xml
<root>
  <record>
    <car_model>Toyota</car_model>
    <year_of_manufacture>2020</year_of_manufacture>
    <price>15000</price>
    <fuel>Petrol</fuel>
  </record>
</root>
```

## License

This is a modified version of code provided as part of IBM’s Data Engineering course material. Use and adapt freely for learning purposes or internal projects.
