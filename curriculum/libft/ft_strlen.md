# ft\_strlen

{% code overflow="wrap" %}
```
STRLEN(3) (simplified)

NAME
    strlen -- find length of string
SYNOPSIS
    size_t(const char *s);
DESCRIPTION
    The strlen() function computes the length of the string s.
RETURN VALUES
    The strlen() function returns the number of characters that precede the terminating NUL character.
```
{% endcode %}

{% hint style="info" %}
To determine the length of a string, ft\_`strlen` scans the string character by character until it reaches the null terminator at the end of the string. It then returns the number of characters that were scanned.
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include "libft.h"

size_t	ft_strlen(const char *s)
{
	size_t	i;

	i = 0;
	while (s[i] != '\0')
		i++;
	return (i);
}
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include <stdio.h>

int main(void)
{
  char *s = "This is a test string";
  int len;

  len = ft_strlen(s);
  printf("Length of string: %d\n", len);

  return (0);
}
```
{% endcode %}

{% code title="output:" overflow="wrap" %}
```
Length of string: 21
```
{% endcode %}

