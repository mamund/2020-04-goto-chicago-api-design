# Company Vocabulary

## Data Elements
 * companyId -> identifier = https://schema.org/identifier
 * companyName -> legalName = https://schema.org/legalName
 * streetAddress -> streetAddress = https://schema.org/streetAddress
 * city -> locality = https://schema.org/addressLocality
 * stateProvince -> addressRegion = https://schema.org/addressRegion
 * postalCode -> postalCode = https://schema.org/postalCode
 * country -> addressCountry = https://schema.org/addressCountry
 * telephone -> telephone = https://schema.org/telephone
 * email -> email = https://schema.org/email
 * status (suspended, active, pending,closed) -> status = https://schema.org/status
 * dateCreated -> dateCreated = https://schema.org/dateCreated
 * dateUpdated -> dateMOdified = https://schema.org/dateModified

## Action Elements
 
 * list
 * create
   * legalName[R], streetAddress, locality, addressRegion, postalCode, 
      addressCountry(US), telephone, email[R], status(pending)[R]
 * read
   * identifier[R]
 * update
   * identifier[R], legalName[R], streetAddress, locality, addressRegion, 
      postalCode, addressCountry(US), telephone, email[R], status[R]
 * delete
   * identifier[R]
 * filter 
   * status, addressCountry, addressRegion, legalName

