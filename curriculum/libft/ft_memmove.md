# ft\_memmove

{% code overflow="wrap" %}
```
MEMMOVE(3) (simplified)

NAME
    memmove -- copy byte string
SYNOPSIS
    void *memmove(void *dst, const void *src, size_t len);
DESCRIPTION
    The memmove() function copies len bytes from string src to string dst.
    The two strings may overlap; the copy is always done in a non-destructive manner.
RETURN VALUES
    The memmove() function returns the original value of dst.
```
{% endcode %}

{% hint style="info" %}
To implement `ft_memmove`, you will need to ensure that the function handles the case where the source and destination memory blocks overlap correctly. To do this, you will need to copy the bytes from the source to the destination using a loop, starting with the last byte and working your way backwards to the first byte. This will ensure that the bytes are copied in the correct order and that the original data is not overwritten before it has been copied.
{% endhint %}

Suppose we have an array of 5 chars, where each char is a byte long

{% hint style="info" %}
```c
+++++++++++++++++++++++++++++++
| 'a' | 'b' | 'c' | 'd' | 'e' |
+++++++++++++++++++++++++++++++
 0x100 0x101 0x102 0x103 0x104
```
{% endhint %}

Now according to the man page of `memcpy`, it takes 3 arguments, a pointer to the destination block of memory, a pointer to the source block of memory, and the size of bytes to be copied.

What if the destination is `0x102`, the source is `0x100` and the size is `3` ?\
Memory overlapping happens here. That is, `0x100` would be copied into `0x102`, `0x101` would be copied into `0x103` and `0x102` would be copied into `0x104`.

Notice that we first copied into `0x102` then we copied from `0x102` which means that the value which was originally in `0x102` was lost as we overwrote it with the value we copied into `0x102` before we copy from it. So we would end up with something like

{% hint style="info" %}
{% code overflow="wrap" %}
```c
+++++++++++++++++++++++++++++++
| 'a' | 'b' | 'a' | 'b' | 'a' |
+++++++++++++++++++++++++++++++
 0x100 0x101 0x102 0x103 0x104
```
{% endcode %}
{% endhint %}

Instead of

{% hint style="info" %}
{% code overflow="wrap" %}
```c
+++++++++++++++++++++++++++++++
| 'a' | 'b' | 'a' | 'b' | 'c' |
+++++++++++++++++++++++++++++++
 0x100 0x101 0x102 0x103 0x104
```
{% endcode %}
{% endhint %}

According to its man page, it first copies the bytes to be copied into a temporary array then pastes them into the destination block as oppose to a function like `memcpy` which copies directly from the source block to the destination block.



{% code overflow="wrap" lineNumbers="true" %}
```c
#include "libft.h"

void    *ft_memmove(void *dst, const void *src, size_t len)
{
    char    *p_src;
    char    *p_dst;
    size_t    i;
    
    if (!dst && !src)
        return (NULL);
    p_src = (char *) src;
    p_dst = (char *) dst;
    i = 0;
    /* copy from end to start */ 
    if (p_dst > p_src)
        while (len-- > 0)
            p_dst[len] = p_src[len];
    /* copy from start to end, like we're used to */
    else
    {
        while (i++ < len)
            p_dst[i] = p_src[i];
    }
    return (dst);
}

    /* declare a temporary pointer for dst */
    /* declare a temporary pointer for src */  
    /* if src and dst are NULL, return dst */
    /* make dst tmp pointer equal to dst converted to unsigned char */
    /* make src tmp pointer equal to src converted to unsigned char */
    /* loop over the dst tmp pointer while we didn't reach n */
    /* set the current byte of dst tmp pointer equal to current byte of src tmp pointer */
    /* return dst */
```
{% endcode %}

{% code overflow="wrap" lineNumbers="true" %}
```c
#include <stdio.h>

int main(void) {
  char src[] = "This is a test";
  char dst[20];

  ft_memcpy(dst, src, sizeof(src));
  printf("dst before overlap: %s\n", dst);

  ft_memmove(dst, dst + 5, 10);
  printf("dst after overlap: %s\n", dst);

  return (0);
}

```
{% endcode %}

{% code title="output:" %}
```
dst before overlap: This is a test
dst after overlap: is a test

```
{% endcode %}

{% hint style="info" %}
As you can see, the ft\_`memmove` function is used to copy the second half of the `src` array to the beginning of the `dst` array, effectively shifting the contents of the array to the left. Since the source and destination memory blocks overlap, ft\_`memmove` handles the copy correctly by copying the bytes in the correct order and preserving the original data.
{% endhint %}
