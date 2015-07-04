# EntityFramework.IndexingExtensions
Indexing Extensions for Entity Framework 6


### Installation

```
PM> Install-Package EntityFramework.IndexingExtensions
```

### Usage

``` csharp
public class MyDataContext : DbContext
{
  protected override void OnModelCreating(DbModelBuilder modelBuilder)
  {
    modelBuilder.Entity<Customer>()
        .HasIndex("IX_Customers_Name",          // Provide the index name.
            e => e.Property(x => x.LastName),   // Specify at least one column.
            e => e.Property(x => x.FirstName))  // Multiple columns as desired.

        .HasIndex("IX_Customers_EmailAddress",  // Supports fluent chaining for more indexes.
            IndexOptions.Unique,                // Supports flags for unique and clustered.
            e => e.Property(x => x.EmailAddress)); 
  }
}
```

### Notes

After publishing this, I was informed that there is an active pull request [here](https://entityframework.codeplex.com/SourceControl/network/forks/BrandonDahler/EntityFramework/contribution/7954) to add something similar directly into Entity Framework.  If/when that is merged, you should probably use it instead.  Though, this one should continue to work without issue.
