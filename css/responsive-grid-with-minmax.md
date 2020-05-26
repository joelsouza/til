# Responsive grid with CSS grid repeat + minmax

![](https://miro.medium.com/max/1400/1*eaNO_EZBnvYyGM9q4TslVA.gif)

```css
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```