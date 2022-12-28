# ft\_isprint

{% code overflow="wrap" lineNumbers="true" %}
```
ISPRINT(3) (simplified)

NAME
    isprint -- printing character test (space character inclusive)
SYNOPSIS
    int isprint(int c)
DESCRIPTION
    The isprint() function tests for any printing character, including space. The value of the argument must representable as an unsigned char or the value of EOF.
RETURN VALUES
    The isprint() function returns zero if the character tests false and returns non-zero if the character tests true.
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include "libft.h"

int	ft_isprint(int c)
{
	if (c >= 32 && c <= 126)
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
	printf("%d", ft_isprint('g'));
}
```
{% endcode %}
