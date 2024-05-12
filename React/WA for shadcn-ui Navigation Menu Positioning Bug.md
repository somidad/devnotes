
## Demo

![](https://private-user-images.githubusercontent.com/8351234/263900034-6b5e7fc3-82e3-42a2-baf6-415b1e8c81b9.gif?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTU1MTg0ODgsIm5iZiI6MTcxNTUxODE4OCwicGF0aCI6Ii84MzUxMjM0LzI2MzkwMDAzNC02YjVlN2ZjMy04MmUzLTQyYTItYmFmNi00MTViMWU4YzgxYjkuZ2lmP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MDUxMiUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDA1MTJUMTI0OTQ4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NzAxZjIyYTE0OWY2NTc1ZTU2MTFkMDZmMjBhNjkyZDE5MDEyNTQ4ZDY4YTZiZTExM2YxODliNjAxNmI2ZDAzYSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmYWN0b3JfaWQ9MCZrZXlfaWQ9MCZyZXBvX2lkPTAifQ.k9P1MwWxFuQa2259rOCx1cCc9P5Cfo6mkvLSosNcJ7k)

- https://github.com/AdiRishi/shadcn-navbar-bug-demo

## Workaround

```diff
 <NavigationMenu>
   <NavigationMenuList>
+    <NavigationMenu>
     <NavigationMenuItem>
       <NavigationMenuTrigger>Trigger</NavigationMenuTrigger>
       <NavigationMenuContent>
         <NavigationMenuLink>Link 1</NavigationMenuLink>
         <NavigationMenuLink>Link 2</NavigationMenuLink>
         <NavigationMenuLink>Link 3</NavigationMenuLink>
       </NavigationMenuContent>
     </NavigationMenuItem>
+    </NavigationMenu>
   </NavigationMenuList>
 </NavigationMenu>
```