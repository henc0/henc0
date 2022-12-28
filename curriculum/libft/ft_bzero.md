# ft\_bzero

{% code overflow="wrap" %}
```
BZERO(3) (simplified)

NAME
    bzero -- write zeroes to a bye string
SYNOPSIS
    void bzero(void *s, size_t n);
DESCRIPTION
    The bzero() function writes n zeroed bytes to the string s. If n is zero, bzero() does nothing.
```
{% endcode %}

{% hint style="info" %}
This function works the same way as the ft\_`memset`, except you don't have to specify what character to write, it'll always be `0` (`NUL` character).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include "libft.h"

void	ft_bzero(void *s, size_t n)
{
	size_t	i;
	char	*ptr;

	ptr = (char *)s;
	i = 0;
	while (i < n)
	{
		ptr[i] = 0;
		i++;
	}
}
```
{% endcode %}

{% code title="output:" %}
```
Buffer before ft_bzero: This is a test
Buffer after ft_bzero:
```
{% endcode %}

{% hint style="info" %}
As you can see, `ft_bzero` is used to clear the first 10 bytes of the `buffer` array, which effectively erases the first 10 characters of the string stored in the array. It is important to note that `ft_bzero` does not clear the null terminator at the end of the string, so the string is still considered to be null-terminated even after the call to `ft_bzero`.

It is also important to note that the `bzero` function has been deprecated in favor of the `memset` function, which provides similar functionality with more flexibility. You may want to consider using ft\_`memset` instead of `ft_bzero` in your own code.
{% endhint %}
