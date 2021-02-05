<!-- .slide: data-background="#4CA737" -->
## Stubbed Section 1

---

## Purpose of Section 1

- Demo some interesting slides that may not be required for the Technical Learning session
- For example, this slide contains speaker notes
 - 	Press the *S* key on your keyboard to open the notes window
- Speaker notes can be included in a PDF render as a separate page after it's corresponding slide   

NOTE:
- Speaker notes can be the narration script used in a recorded video. The narration script speakers notes can be included in a rendered PDF of the deck. The output PDF is a useful student course book.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque eget lacus mollis, semper magna tempus, blandit ligula. Mauris sed euismod ante, sed finibus nisl. Mauris gravida consequat dignissim. Phasellus eu rhoncus sem. Morbi in dolor aliquet, maximus libero maximus, ultrices arcu. Aliquam ornare nec eros quis laoreet. Curabitur sit amet posuere lacus. In hac habitasse platea dictumst. Integer mi metus, ultrices non odio quis, gravida placerat enim. Nulla ac dignissim est. Nullam semper vehicula quam, id pulvinar massa ornare nec.

Nulla eleifend posuere magna in gravida. Duis feugiat pellentesque dolor sit amet dictum. Sed lacus diam, lacinia vel mauris et, blandit accumsan turpis. Nunc fringilla felis quam, vel mattis leo consectetur non. Mauris fermentum purus arcu, eu tincidunt leo maximus ut. Nulla pretium tellus tristique ante volutpat, eget fringilla arcu efficitur. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque luctus suscipit lorem sed gravida. Quisque congue tellus et ex blandit facilisis. Ut sit amet magna ac lorem congue laoreet a eu eros. Sed non mauris tempor, varius magna nec, maximus lorem. Etiam dignissim leo id augue porttitor vestibulum eget non ante. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Pellentesque mattis fermentum libero, nec mollis tellus eleifend ac. Nunc porttitor purus in nibh sagittis convallis. Integer vehicula lacinia sapien, ut facilisis orci.

Phasellus tempor porta odio sed imperdiet. Quisque arcu leo, volutpat id purus eget, ullamcorper elementum massa. Sed a neque a dolor aliquet pretium non non lectus. Etiam leo augue, semper eget ornare eu, euismod ut mauris. Integer orci mauris, egestas id orci non, vehicula gravida leo. Ut iaculis urna dictum tellus egestas, vitae tempus sem mattis. Pellentesque erat odio, congue in laoreet quis, viverra sed metus. Cras sodales lorem erat, in viverra mi euismod vitae. Phasellus leo metus, varius id maximus eu, vulputate ullamcorper erat.

Integer nunc leo, ultrices sit amet risus vel, ultricies faucibus enim. Sed mi lorem, consectetur eget faucibus nec, vestibulum ut elit. Suspendisse potenti. Praesent ut eros ut arcu tincidunt convallis. Curabitur quis dui dignissim, lobortis urna eu, dictum tellus. Vivamus sagittis pulvinar faucibus. Donec placerat a ante porttitor pharetra. Vestibulum sagittis enim id orci consequat tristique. Integer sit amet rutrum nulla, et condimentum felis. Morbi at ipsum enim. Praesent id lacus neque. Cras convallis interdum lectus sit amet fermentum.

---

## JAVA example

``` java
/**
 * Main class for the basic JDBC example.
 **/
public class BasicExample {

    public static void main(String[] args) {

        // Configure the database connection.
        PGSimpleDataSource ds = new PGSimpleDataSource();
        ds.setServerNames(new String[]{"localhost"});
        ds.setPortNumbers(new int[]{26257});
```

---

## Highlighted Java Code Example

``` java [1-3|4|5-6|7-8]
long transferResult = 
    runTX(session, transferFunds(
        fromAccountId, toAccountId, transferAmount));
 if (transferResult != -1) {
    long fromBalanceAfter =
       runTX(session, getAccountBalance(fromAccountId));
    long toBalanceAfter =
       runTX(session, getAccountBalance(toAccountId));
 }
```


---

## GO example

``` go
import (
    "context"
    "fmt"
    "log"

    "github.com/cockroachdb/cockroach-go/v2/crdb/crdbpgx"
    "github.com/jackc/pgx/v4"
)

func transferFunds(ctx context.Context, tx pgx.Tx, from int, to int, amount int) error {
    // Read the balance.
    var fromBalance int
    if err := tx.QueryRow(ctx,
        "SELECT balance FROM accounts WHERE id = $1", from).Scan(&fromBalance); err != nil {
        return err
    }

```
---

## Sources from single elements

``` scala
val source: Source[String, NotUsed] = Source.single(
  "Hello World"
)
```

``` scala
val source: Source[String, NotUsed] = Source.repeat(
  "Hello World"
)
```

- single
	- *Push* a single element and then *complete*.
- something else
	- else

---

## Table Example

| Left Aligned  | Center Aligned  | Right Aligned |
|:------------- |:---------------:| -------------:|
| col 3 is      | some wordy text |         $1600 |
| col 2 is      | centered        |           $12 |
| zebra stripes | are neat        |            $1 |

NOTE: The left- and right-most pipes (|) are only aesthetic, and can be omitted. The spaces don't matter, either. Alignment depends solely on : marks.

---

## Lists Example

- Lists must be preceded by a blank line
- Unordered lists start each item with a `-` (or `*`)
	- Indent a level to make a nested list
		1. Ordered lists are supported.
		2. Start each item (number-period-space) like `1. `
		42. Funny but it doesn't matter what number you use, it will render sequentially
		1. If possible, it's good idea to use sequential #s for source readability

---

## Block Quote

> Angle brackets `>` are used for block quotes.  

---

## Nested Block Quote

> > Block quotes can be nested.  
> > > Multiple Levels
