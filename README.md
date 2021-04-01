# csv

This is a copy of the standard go csv writer with only one change. A callback function has been added to the Writer so users can decide whether a field should be quoted or not.

## Usage

```
go get github.com/asimlqt/csv
```

The callback takes 2 arguments, `n` is the index of the field starting at zero and `field` is the actual value that is to be output.
The following example will add quotes around the column in the csv.

```
writer := csv.NewWriter(file)
writer.NeedsQuotes = func(n int, field string) bool {
	if n == 0 {
		return true
	}
	return false
}
```
