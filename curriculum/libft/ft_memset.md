# ft\_memset

{% code overflow="wrap" %}
```
MEMSET(3) (simplified)

NAME
    memset -- fill a byte string with a byte value
SYNOPSIS
    void *memset(void *s, int c, size_t n);
DESCRIPTION
    The memset() function writes len bytes of value c (converted to an unsigned char) to the string s.
RETURN VALUES
    The memset() function returns its first argument.

```
{% endcode %}

{% hint style="info" %}
can be used to initialize a block of memory to a specific value, or to set specific values within a block of memory. It is often used to clear buffers or arrays, or to set specific bits in a block of memory to specific values
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include "libft.h"

void	*ft_memset(void *s, int c, size_t n)
{
	size_t	i;
	char	*ptr;

	ptr = (unsigned char *)s;
	i = 0;
	while (i < n)
	{
		ptr[i] = (unsigned char) c;
		i++;
	}
	return (s);
}
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
  char buffer[100];

  ft_memset(buffer, 0, 100);
  printf("Buffer after ft_memset: %s\n", buffer);

  strcpy(buffer, "This is a test");
  printf("Buffer after strcpy: %s\n", buffer);

  ft_memset(buffer + 10, '-', 4);
  printf("Buffer after ft_memset: %s\n", buffer);

  return 0;
}
```
{% endcode %}

<pre data-title="ouput:" data-overflow="wrap"><code><strong>Buffer after ft_memset:
</strong>Buffer after strcpy: This is a test
Buffer after ft_memset: This is ----

</code></pre>

