# Set up a media library in drupal

## Objective

Building a media library that can preserving images and embed the images into article's body (content editing area).

## Related modules

#### Download & install

* [media_entity](https://www.drupal.org/project/media_entity)
  ( ceate a media entity )
* [media_entity_image](https://www.drupal.org/project/media_entity_image)
  ( give image property in media entity )
* [entity_embed](https://www.drupal.org/project/entity_embed)
  ( allow embeding entity in content area )
* [entity_browser](https://www.drupal.org/project/entity_browser)
  ( provide the entity browser / picker )
* [ctools](https://www.drupal.org/project/ctools)
  ( something entity_browser needs )
* [inline_entity_form](https://www.drupal.org/project/inline_entity_form)
  ( something Entity Browser IEF needs )

#### Install

* Entity Browser IEF
  ( can create new entity in entity browser )

## Steps

### Create a image bundle

1. [ Structure ] >> [ Media bundles ]  
	``Add media bundle``  
	Type provider :: ``Image``

2. Add media bundle field  
	Reference``Image``  
	:``no``: Enable Alt field

3. [ media bundle ] >> [ Edit ]  
	Field with source information

### Create media form view

4. [ Structure ] >> [ Display modes ] >> [ Form modes ]  
	``Add new form mode`` :: ``Media``  
	[ Structure ] >> [ Media bundles ]  
	``Manage form display``  
	CUSTOM DISPLAY SETTINGS :: ``Media browser form``  
	Manage Media browser form

5. [ Structure ] >> [ Views ]  
	``Add new view``  
	VIEW SETTINGS :: Show: ``Media`` of type ``image``  
	``+Add`` :: ``Entity Browser``  
	FORMAT :: ``Grid``  
	FIELDS :: ``Thumbnail`` , ``Entity browser bulk select form``

### Create entity browser

6. [ Configuration ] >> [ Content authoring ] >> [ Entity browsers ]  
	``Add Entity browser``  
　		Display plugin :: ``iFrame``  
　		Widget selector plugin :: ``Tabs``  
　		Selection display plugin :: ``No selection display``  
	Display :``yes``: Auto open entity browser  
	Add widget plugin  
　		View :: ``Media Browser View``  
　		Entity form :: ``Media`` , ``image``

7. [ Configuration ] >> [ Content authoring ] >> [ Text editor embed buttons ]  
	``Add embed button``  
	Embed type :: ``Entity``  
	Entity type :: ``Media``  
	Entity browser :: ``Image browser``  
	ENTITY BROWSER SETTINGS :``yes``: Display the entity after selection

8. [ Configuration ] >> [ Content authoring ] >> [ Text formats and editors ]  
	``Drag the button``  
	Enabled filters :``yes``: Display embedded entities  
	Limit allowed HTML tags ``<drupal-entity data-*>``
