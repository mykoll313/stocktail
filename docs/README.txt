STOCKTAIL QR RECIPE LANDING PAGE

1. Host recipe.html and index.html on an HTTPS static website (for example, GitHub Pages).
2. If using GitHub Pages in repository StockTail, place these files in docs/ and configure Settings > Pages > Deploy from branch > main > /docs.
3. After publishing, test https://YOUR-USERNAME.github.io/StockTail/recipe.html?cocktail_id=16 (replace username and ID).
4. In lib/pb06/pb06_landscape_display.dart set:
   const String recipeSharePageUrl = 'https://YOUR-USERNAME.github.io/StockTail/recipe.html';
5. Confirm the public-facing role can execute get_stocktail_cocktails and can read only intended data under RLS. IMPORTANT: the current function returns inventory data and locations for ALL eligible cocktails. For production, make a restricted public recipe endpoint returning only approved customer-visible fields.
6. The current QR items payload maps ingredient IDs to inventory IDs. If the same ingredient occurs multiple times in a recipe, update the QR payload to use cocktailIngredientId and return it from SQL.
7. If image_path uses another bucket, update imageUrl() in recipe.html.
8. The site shows only products with positive quantity_on_hand and validates that selected inventory IDs belong to the returned ingredient products.
9. No prices are shown because the current SQL function does not return prices.
10. Do not put service-role/secret keys in static website files.
