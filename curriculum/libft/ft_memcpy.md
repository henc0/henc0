# ft\_memcpy

{% code overflow="wrap" %}
```
MEMCPY(3) (simplified)

NAME
    memcpy -- copy memory area
SYNOPSIS
    void *memcpy(void *dst, const void *src, size_t n);
DESCRIPTION
    The memcpy() function copies n bytes from memory area src to memory area dst. If dstt and src overlap, behavior is undefined. Applications in which dst and src might overlap should use memove(3) instead.
RETURN VALUES
    The memcpy() function returns the original value of dst
```
{% endcode %}

{% hint style="info" %}
The `memcpy` function copies maximum n bytes from `src` to `dst`.

This functions works like the `strcpy` function, except that `memcpy` accepts `void *` as parameters, so we can give it any type of pointer we want to copy.
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include "libft.h"

void	*ft_memcpy(void *dst, const void *src, size_t n)
{
	size_t	i;
	unsigned char	*dst_ptr;
	unsigned char	*src_ptr;

    if (dst == (void *)0 && src == (void *)0)
	return (dst);
	dst_ptr = (unsigned char *)dst;
	src_ptr = (unsigned char *)src;
	i = 0;
	while (i < n)
	{
		dst_ptr[i] = src_ptr[i];
		i++;
	}
	return (dst);
}
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include <stdio.h>

int main(void)
{
  char src[] = "This is a test";
  char dst[20];

  ft_memcpy(dst, src, sizeof(src));
  printf("dst before overlap: %s\n", dst);

  ft_memcpy(dst, dst + 5, 10);
  printf("dst after overlap: %s\n", dst);

  return (0);
}
```
{% endcode %}

{% code title="output:" %}
```
dst before overlap: This is a test
dst after overlap: 
```
{% endcode %}

{% hint style="info" %}
As you can see, the `memcpy` function is used to copy the second half of the `src` array to the beginning of the `dst` array, effectively shifting the contents of the array to the left. Since the source and destination memory blocks overlap, `memcpy` does not handle the copy correctly and the original data is overwritten before it has been copied.
{% endhint %}

{% hint style="info" %}
It is important to note that `ft_memcpy` does not copy the null terminator at the end of the string, so the `dst` array is not necessarily null-terminated after the call to `ft_memcpy`. You will need to ensure that the `dst` array is properly null-terminated if this is necessary.

It is also important to note that the size of the `dst` array must be at least as large as the size of src.
{% endhint %}
