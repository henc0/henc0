# ft\_isascii

{% code overflow="wrap" %}
```
ISASCII(3) (simplified)

NAME
    isascii -- test for ASCII character
SYNOPSIS
    int isascii(int c)
DESCRIPTION
    The isascii() function tests for an ASCII character, which is any character between 0 and octal 0177 inclusive.
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include "libft.h"

int	ft_isascii(int c)
{
	if (c >= 0 && c <= 127)
		return (1);
	return (0);
}
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include <stdio.h>

int	main(void)
{
	printf("%d", ft_isascii('s'));
}
```
{% endcode %}
