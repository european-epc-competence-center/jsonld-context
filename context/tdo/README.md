# TDO Jewelry JSON-LD Context

This directory contains a JSON-LD context definition for **Tortuga de Oro (TDO)** specific to jewelry and precious metals products. The context extends standard vocabularies (Schema.org and GS1) with domain-specific properties that are not covered by existing standards.

## Files in this Directory

- **`goldring.jsonld`** - The main JSON-LD context definition file
- **`goldring-example.jsonld`** - Complete example showing how to use the context with real product data
- **`README.md`** - This documentation file

## Purpose

Standard vocabularies like Schema.org provide general product properties but lack specific terminology for jewelry industry requirements such as:
- Precious metal purity standards (millesimal fineness)
- Ring sizing systems and measurements
- Hallmarks and inside markings
- Fairtrade certification for ethical sourcing
- Surface finish treatments

This TDO context fills these gaps while maintaining compatibility with standard vocabularies.

## Key Features

- **Millesimal fineness** standard for gold purity (e.g., 585 = 14k gold)
- **Fairtrade certification** properties for ethical sourcing
- **Ring-specific measurements** (inner diameter, ring size systems including ISO 8653)
- **Inside markings** and engravings (hallmarks, logos, laser engravings)
- **Gold content** percentage and weight calculations
- **Surface finish** properties (polished, matte, brushed, hammered)

## Quick Navigation

- [Structure](#structure)
- [Coverage Analysis](#coverage-analysis)
  - [Properties Covered by Standards](#properties-covered-by-standard-vocabularies)
  - [Custom TDO Properties](#custom-properties-not-covered-by-standards)
- [Material Standards](#material-standards-referenced)
- [Usage Examples](#usage-example)
- [How to Use](#how-to-use-this-context)
- [References](#references)

## Structure

This vocabulary follows the same structure as the [Schema.org vocabulary](https://schema.org/), using:
- Standard RDF/RDFS property definitions
- `@graph` array containing all property and class definitions
- Proper `schema:domainIncludes` and `schema:rangeIncludes` declarations
- `rdfs:label` and `rdfs:comment` for human-readable documentation

The context includes common namespace prefixes including `schema` for `https://schema.org/`.

## Coverage Analysis

### Properties Covered by Standard Vocabularies

**Schema.org:**
- `sku` - Product identifier / Stock Keeping Unit
- `productionDate` - Manufacturing date
- `size` - General size property
- `weight` - Product weight
- `height` - Height dimension
- `width` - Width dimension  
- `material` - Base material property

**GS1 Web Vocabulary:**
- `gtin` - Global Trade Item Number (alternative to SKU)

### Custom Properties (Not Covered by Standards)

The following properties are specific to jewelry and precious metals and have been added to the TDO namespace:

#### Gold & Precious Metal Properties

1. **`fineness`** (integer)
   - Millesimal fineness of precious metal (parts per 1000)
   - Example: 585 for 14k gold (58.5% gold)
   - Standard: European hallmarking convention
   - Common values: 333 (8k), 375 (9k), 417 (10k), 585 (14k), 750 (18k), 916 (22k), 999 (24k)

2. **`goldContentPercentage`** (decimal)
   - Percentage of gold content
   - Example: 58.5 for 585/1000 fineness

3. **`goldContentWeight`** (QuantityValue)
   - Absolute weight of gold in the item
   - Useful for calculating gold value

4. **`surfaceFinish`** (string)
   - Surface treatment: polished, matte, brushed, hammered, etc.
   - In German: poliert, matt, gebürstet, gehämmert

#### Ring-Specific Properties

5. **`innerDiameter`** (QuantityValue)
   - Inner diameter of the ring
   - German: Durchmesser innen

6. **`slotWidth`** (QuantityValue)
   - Width of slot or groove in the ring
   - German: Schlitz

7. **`ringSize`** (string)
   - Ring size in specific sizing system
   - Example: "50" for D/EU system

8. **`ringSizeSystem`** (string)
   - Ring sizing system: D/EU, US, UK, ISO 8653
   - ISO 8653: International ring size standard

#### Markings & Features

9. **`insideFeatures`** (string)
   - Free-text description of inside features
   - German: Merkmale Innenseite

10. **`insideMarkings`** (array of StructuredValue)
    - Structured list of markings with types
    - Types: logo, hallmark, stamp, engraving

11. **`markingType`** (string)
    - Type of marking: logo, hallmark, stamp, engraving

12. **`marking`** (string)
    - Content of the marking

#### Certification Properties

13. **`fairTradeCertified`** (boolean)
    - Whether precious metal is Fairtrade certified
    - Fairtrade Gold ensures ethical sourcing

14. **`fairTradeRegistration`** (string)
    - Fairtrade certification number

## Material Standards Referenced

### Millesimal Fineness System
The standard system for expressing precious metal purity in parts per 1000:
- Used in European hallmarking
- 585 = 585/1000 = 58.5% gold = 14 karat
- More precise than karat system

### Alternative Material Classification Systems

While not directly encoded in this context, these standards can be referenced via `eclassCode`:

1. **ECLASS** - ISO-compliant material classification system
   - Widely used in e-commerce and industry
   - Provides standardized codes for materials

2. **ISO 10303 (STEP)** - Standard for the Exchange of Product model data
   - Computer-interpretable product data representation

3. **IEC 61360** - Standard data element types with associated classification scheme

### Fairtrade Gold Certification
- Ensures ethical mining practices
- Guarantees fair wages and working conditions
- Environmental standards for mining operations
- Traceable supply chain from mine to product

## Usage Example

See [`goldring-example.jsonld`](goldring-example.jsonld) for a complete example of how to use this context with actual product data.

## How to Use This Context

### In JSON-LD Documents

Reference the context in your JSON-LD documents:

```json
{
  "@context": [
    "https://schema.org/",
    "https://european-epc-competence-center.github.io/jsonld-context/context/tdo/goldring.jsonld"
  ],
  "@type": "Product",
  "sku": "GR-585-50",
  "fineness": 585,
  "ringSize": "50"
}
```

### Development/Testing

For local development, you can reference the context file directly:

```json
{
  "@context": [
    "https://schema.org/",
    "./goldring.jsonld"
  ]
}
```

## References

- Schema.org Product: https://schema.org/Product
- GS1 Web Vocabulary: https://www.gs1.org/voc/
- QUDT Ontology (units): http://qudt.org/
- ISO 8653: Ring sizing standard
- ECLASS: https://www.eclass.eu/
- Fairtrade Gold: https://www.fairtrade.net/product/gold



