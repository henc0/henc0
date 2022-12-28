# ft\_isalnum

### Subject

{% code overflow="wrap" %}
```
ISALNUM(3) (simplified)

NAME
    isalnum -- alphanumeric character test
SYNOPSIS
    int isalnum(int c)
DESCRIPTION
    The isalnum() function tests for any character for which isalpha(3) or isdigit(3) is true. The value of the argument must be representable as an unsigned char or the value of EOF.
RETURN VALUES
    The isalnum() function returns zero if the character tests false and returns non-zero if the character tests true.
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include "libft.h"

int    ft_isalnum(int c)
{
    if (ft_isalpha(c) || ft_isdigit(c))
        return (c); 
    return (0);
}
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include <stdio.h>

int	main(void)
{
	printf("%d", ft_isalnum(42));
}
```
{% endcode %}

