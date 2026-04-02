# ApiCheck Make (Integromat) Integration

Address validation, search, and verification for 18 European countries.

## Installation

Search for "ApiCheck" in Make's app directory and connect your account.

## Credentials

1. Get your API key from [app.apicheck.nl](https://app.apicheck.nl)
2. In Make, add ApiCheck as a connection
3. Enter your API key

## Modules

### Global Search (Recommended)

The **Global Search** module is the most powerful way to find addresses. It searches across streets, cities, and postal codes in one query with powerful filtering options.

**Use Global Search when you want to:**
- Find any type of address data (streets, cities, or postal codes)
- Filter results by city, street, or postal code area
- Search across Belgium with locality/municipality filters
- Get flexible, comprehensive results in one call

**Configuration:**
- **Country**: Select from 18 European countries
- **Search Query**: Enter a street name, city name, or postal code
- **Limit**: Maximum number of results (default: 10)

**Advanced Filtering** (combine with search query):
- **Filter by City ID** - only return results within a specific city
- **Filter by Street ID** - only return results on a specific street
- **Filter by Postal Code ID** - only return results in a postal code area
- **Filter by Locality ID (Belgium)** - only return results in a locality (deelgemeente)
- **Filter by Municipality ID (Belgium)** - only return results in a municipality (gemeente)

**Result Types:**
Each result includes a `type` field:
- `city` - City/municipality
- `street` - Street name
- `postalcode` - Postal code area

**Example Workflow:**
1. Use Global Search to find cities matching "Amsterdam"
2. Get the `city_id` from the result
3. Use Global Search again with `city_id` filter to find streets in that city

### Lookup Address

Look up an exact address by postal code and house number.

**Supported countries:** Netherlands, Luxembourg

**Fields:**
- Country
- Postal Code (e.g., 1012LM)
- House Number (e.g., 1)
- Number Addition (optional, e.g., A, B, 1-3)

### Get Number Additions

Get available number additions (apartment/suite letters) for a postal code and house number.

**Supported countries:** Netherlands, Luxembourg

### Verify Email

Verify an email address for validity and check if it's from a disposable email provider.

**Returns:**
- Status: valid, invalid, or unknown
- Disposable email flag
- Greylist status

### Verify Phone

Verify a phone number for validity.

**Fields:**
- Phone Number (include country code, e.g., +31612345678)

**Returns:**
- Valid/invalid status
- Country code
- Formatted number

### Search City

Search for cities by name across 18 European countries.

### Search Street

Search for streets by name. Optionally filter by city.

### Search Postal Code

Search for postal codes. Optionally filter by city.

### Search Locality

Search for localities (deelgemeenten) by name. Primarily for Belgium.

### Search Municipality

Search for municipalities (gemeenten) by name. Primarily for Belgium.

### Search Address

Resolve a full address using IDs from other search modules.

**Fields:**
- Street ID (from Search Street)
- City ID (from Search City)
- Postal Code ID (from Search Postal Code)
- Locality ID (from Search Locality, Belgium)
- Municipality ID (from Search Municipality, Belgium)
- House Number
- Number Addition
- Limit

## Supported Countries

### All Search Modules (18 countries)
Netherlands (nl), Belgium (be), Luxembourg (lu), Germany (de), France (fr), Czech Republic (cz), Finland (fi), Italy (it), Norway (no), Poland (pl), Portugal (pt), Romania (ro), Spain (es), Switzerland (ch), Austria (at), Denmark (dk), United Kingdom (gb), Sweden (se)

### Address Lookup (Netherlands & Luxembourg only)
Netherlands (nl), Luxembourg (lu)

## Example Scenarios

### Find addresses in a city
1. **Global Search** - Search for "Amsterdam", get `city_id`
2. **Global Search** - Search for "Dam" with `city_id` filter, get `street_id`
3. **Search Address** - Use `street_id` and house number to get full address

### Validate customer address
1. **Lookup Address** - Enter postal code and house number
2. If multiple units exist, use **Get Number Additions** to show options
3. **Verify Email** - Validate the customer's email address
4. **Verify Phone** - Validate the customer's phone number

### Belgium address search
1. **Search Municipality** - Find the municipality (gemeente)
2. **Search Locality** - Find the locality (deelgemeente) if needed
3. **Global Search** - Use `municipality_id` or `locality_id` filter for precise results

## Tips

1. **Use Global Search first** - It's the most flexible and covers all use cases
2. **Filter for precision** - Use city_id, street_id, etc. to narrow down results
3. **Chain modules** - Use IDs from one search as filters in another
4. **Belgium addresses** - Use locality and municipality filters for precise results

## Support

- Documentation: [docs.apicheck.nl](https://docs.apicheck.nl)
- Support: support@apicheck.nl
