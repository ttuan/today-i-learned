# Create another version from a version image in Carrierwave

Carrierwave has an option, which allows us to create a new version from a
processed version with key word: `from_version`

```ruby
version :optimized do
  process :pngquant
  process :optimize
  process :store_geometry
end

version :large, from_version: :optimized do
  process resize_to_limit: [1400, 1400]
  process :store_geometry
end
```
