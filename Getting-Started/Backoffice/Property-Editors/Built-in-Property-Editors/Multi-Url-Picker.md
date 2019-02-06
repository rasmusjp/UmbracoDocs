# Multi Url Picker

`Alias: Umbraco.MultiUrlPicker`

`Returns: IEnumerable<Link> or Link`

Multi Url Picker allows an editor to easily pick and sort multiple urls. These can either be internal, external or media.

## Data Type Definition Example

![Related Links Data Type Definition](images/Related-Links2-DataType.png)

## Content Example 

![Media Picker Content](images/Related-Links2-Content.png)

## MVC View Example - [value converters enabled](../../../Setup/Upgrading/760-breaking-changes.md#property-value-converters-u4-7318)

### Typed:

```csharp
@using Umbraco.Web.Models
@{
    var links = Model.Content.GetPropertyValue<IEnumerable<Link>>("footerLinks");

    if (links.Any())
    {
        <ul>
            @foreach (var link in links)
            {
                <li><a href="@link.Url" target="@link.Target">@link.Name</a></li>
            }
        </ul>
    }
}
```

If `Max number of items` is configured to `1`


```csharp
@using Umbraco.Web.Models
@{
    var link = Model.Content.GetPropertyValue<Link>("link");

    if (link != null)
    {
      <li><a href="@link.Url" target="@link.Target">@link.Name</a></li>
    }
}
```