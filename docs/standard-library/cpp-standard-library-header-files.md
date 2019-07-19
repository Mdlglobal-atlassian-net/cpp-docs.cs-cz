---
title: C++standardní soubory hlaviček knihovny
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: dc337ef078108d86849aa7b7452512dfb69e6e18
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341123"
---
# <a name="c-standard-library-header-files"></a>C++standardní soubory hlaviček knihovny

Hlavičkové soubory pro C++ standardní knihovnu a rozšíření podle kategorie.

## <a name="headers-by-category"></a>Záhlaví podle kategorie

::: moniker range=">=vs-2017"

| Kategorie | Záhlaví |
| - | - |
| [Algoritmy](../cpp/algorithms-modern-cpp.md) | algoritmus > [, cstdlib>\<](cstdlib.md), [ Číselná\<>](numeric.md) [ \<](algorithm.md) |
| Atomické operace |  atomická ><sup>11</sup> [ \<](atomic.md) |
| Obálky knihovny C | [ \<](cfenv.md)<sup></sup> [ \<](cerrno.md) [ \<cassert >](cctype.md), [ccomplex > 11 a b, cctype >, cerrno >, cfenv > 11, \<](ccomplex.md) [ \<](cassert.md)<sup></sup> [ \<cfloat >](cfloat.md),<sup></sup> [ \<cinttypes >](cinttypes.md)11, [ \<ciso646 >](ciso646.md)<sup>b</sup>, [ \<climits >](climits.md), [ \<clocale >](clocale.md), [ cmath\<>](cmath.md), [ csetjmp>,csignal>,cstdalign>11ab,cstdarg>,\<](csetjmp.md) [ \<](cstdarg.md) [ \<](csignal.md) [ \<](cstdalign.md)<sup></sup> [ \<cstdbool >](cstdbool.md)<sup>11 a b</sup>, [ \<cstddef >](cstddef.md), [ \<cstdint >](cstdint.md)<sup>11</sup>, [ \<cstdio >](cstdio.md), [ \<cstdlib >](cstdlib.md), [ CString\<>](cstring.md),<sup></sup> [ \<](ctime.md)<sup></sup> [ \<](cuchar.md) [ \<](cwchar.md) [ ctgmath>11\<](ctgmath.md)a b, CTime – >, cuchar > 11, cwchar >, [ cwctype\<>](cwctype.md) |
| Koncepty | \<Koncepty ><sup>20</sup> |
| [Kontejnery](../cpp/containers-modern-cpp.md) | |
| Kontejnery sekvence | <sup></sup><sup></sup> [ Array\<>](array.md)11, [ deque>,forward_list>11,list>,Vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md) |
| Seřazené asociativní kontejnery| [\<map>](map.md), [\<set>](set.md) |
| Neuspořádané asociativní kontejnery | unordered_map ><sup>11</sup>, [ unordered_set>\<](unordered-set.md)<sup>11</sup> [ \<](unordered-map.md) |
| Adaptéry kontejneru | > fronty, [ \<](queue.md) [ >zásobníku\<](stack.md) |
| Zobrazení kontejneru | \<rozpětí ><sup>20</sup> |
| [Zpracování chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md) | <sup></sup> [ cassert\<>](cassert.md) [, výjimka\<>](exception.md) [, stdexcept\<>](stdexcept.md) [, system_error\<>](system-error.md)11 |
| Obecné nástroje | \<Každý ><sup>17</sup>, [ \<bitset >](bitset.md), \<charconv ><sup>17</sup>, [ \<cstdlib >](cstdlib.md), \<provádění ><sup>17</sup>, [ \<funkční >](functional.md), [ >\<paměti](memory.md), \< [ \<](ratio.md)<sup></sup><sup></sup><sup></sup>memory_resource > 17, volitelné > 17, poměr > 11, scoped_allocator > \< [ \< ](scoped-allocator.md) <sup>11</sup><sup></sup><sup></sup>,<sup></sup> [ \<](type-traits.md) [ \<](typeindex.md) [ \<](utility.md)řazené kolekce členů > 11, type_traits > 11, typeindex > 11, nástroj >, [ \<](tuple.md) \<varianta ><sup>17</sup> |
| [I/O a formátování](../cpp/string-and-i-o-formatting-modern-cpp.md) | <sup></sup><sup></sup> [ \<](iomanip.md) [ \<](fstream.md) [ cinttypes\<>](cinttypes.md)11, [ cstdio>,systémsouborů>17,fstream–>,iomanip>,\<](cstdio.md) [ \<](filesystem.md) [ iOS\<>](ios.md), [ iosfwd>,iostream–>,IStream>,ostream>,sstream>\<](iosfwd.md) [ \<](iostream.md) [ \<](istream.md) [ \<](ostream.md) [ \<](sstream.md) \< [ ,\<streambuf >](streambuf.md) [ ,\<strstream >](strstream.md)<sup>c</sup>, syncstream ><sup>20</sup> |
| Iterátory | [\<iterator>](iterator.md) |
| Podpora jazyků | \< \< \< <sup></sup><sup></sup><sup></sup> [ cfloat\<>](cfloat.md) [, climits\<>](climits.md) [, codecvt\<>](codecvt.md)11 a, porovnat > 20, smlouva > 20, korutina ><sup>20</sup>, [ \<csetjmp >](csetjmp.md), [ \<csignal >](csignal.md), [ \<cstdarg >](cstdarg.md), [ \<cstddef >](cstddef.md), [ \<cstdint > ](cstdint.md) <sup>11</sup><sup></sup> [, cstdlib\<>](cstdlib.md) [, výjimka\<>](exception.md) [, initializer_list\<>](initializer-list.md)11 [, omezení>,\<](limits.md) [ \< New >](new.md), [ \<TypeInfo >](typeinfo.md), \<verze ><sup>20</sup> |
| Lokalizace | [ \<](locale.md) <sup></sup> [ clocale>\<](cvt-wbuffer.md), [codecvt > 11 a, CVT/wbuffer >, CVT/wstring >, národní prostředí > \<](codecvt.md) [ \<](cvt-wstring.md) [ \<](clocale.md) |
| Matematické a číselné znaky | \<bit ><sup>20</sup>, [ \<cfenv >](cfenv.md)<sup>11</sup>, [ \<cmath >](cmath.md), [ \<komplexní >](complex.md), [ \<cstdlib >](cstdlib.md), [ \<omezení >](limits.md), [ Číselná\<>](numeric.md),<sup></sup><sup></sup> [ náhodný\<>](random.md)11 [, poměr>11,valarray>\<](ratio.md) [ \<](valarray.md) |
| [Správa paměti](../cpp/smart-pointers-modern-cpp.md) | <sup></sup><sup></sup> [ přidělování>\<](new.md), \< [ \<](scoped-allocator.md) [ >\<paměti](memory.md), memory_resource > 17, New >, scoped_allocator > 11 [ \<](allocators-header.md) |
| Multithreading | <sup></sup><sup></sup><sup></sup><sup></sup> [ \<](condition-variable.md) [ \<](future.md) [ \<atomická](mutex.md)> 11, condition_variable > 11, budoucí > 11, mutex > 11, [ \<](atomic.md) [ \< shared_mutex >](shared-mutex.md)<sup>14</sup>, [ \<vlákno >](thread.md)<sup>11</sup> |
| Rozsahy | \<rozsahy ><sup>20</sup> |
| Regulární výrazy | regulární výraz ><sup>11</sup> [ \<](regex.md) |
| Řetězce a znaková data | <sup></sup> [ cctype\<>](cctype.md), [ cstdlib>,CString>,cuchar>11,cwchar>,cwctype\<](cstdlib.md) [ \<](cstring.md) [ \<](cuchar.md) [ \<](cwchar.md) [ \< >](cwctype.md) [ ,\<Regex >](regex.md)<sup>11</sup>, [ \<> řetězce](string.md), [ \<string_view >](string-view.md)<sup>17</sup> |
| Time | Chrono ><sup>11</sup>, [ CTime–\<>](ctime.md) [ \<](chrono.md) |

<sup>11</sup> přidáno ve standardu c++ 11. \
<sup>14</sup> přidáno ve standardu c++ 14. \
<sup>17</sup> přidáno ve standardu c++ 17. \
<sup>20</sup> přidáno v konceptu c++ 20 Standard. \
<sup>zastaralé ve</sup> standardu c++ 17. \
<sup>b</sup> odebrána v konceptu c++ 20 Standard. \
Jazyk <sup>c</sup> je zastaralý ve standardu c++ 98.

::: moniker-end

::: moniker range="vs-2015"

|Kategorie|Záhlaví|
|-|-|
|[Algoritmy](../cpp/algorithms-modern-cpp.md)|[\<> algoritmu](algorithm.md)|
|Obálky knihovny C|[ cassert\<>](cassert.md), [ cctype>,cerrno>,cfenv>,cfloat>,cinttypes>,\<](cctype.md) [ \<](cerrno.md) [ \<](cfenv.md) [ \<](cfloat.md) [ \<](cinttypes.md) [ ciso646\<>](ciso646.md) [, climits\<>](climits.md) [, clocale\<>](clocale.md) [, cmath\<>](cmath.md) [, csetjmp\<>](csetjmp.md), [csignal \< >](csignal.md) [ ,\<cstdarg >](cstdarg.md) [ ,\<cstdbool >](cstdbool.md) [ ,\<cstddef >](cstddef.md), [ \<cstdint >](cstdint.md), [ \<cstdio >](cstdio.md), [ cstdlib\<>](cstdlib.md), [ CString>,ctgmath>,CTime–>,cwchar>,cwctype>\<](cstring.md) [ \<](ctgmath.md) [ \<](ctime.md) [ \<](cwchar.md) [ \< ](cwctype.md)|
|[Kontejnery](../cpp/containers-modern-cpp.md)||
|Kontejnery sekvence|[ Array\<>](array.md), [ deque>,forward_list>,list>,Vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md)|
|Seřazené asociativní kontejnery| [\<map>](map.md), [\<set>](set.md)|
|Neuspořádané asociativní kontejnery|unordered_map >, [ \<](unordered-map.md) [ unordered_set>\<](unordered-set.md)|
|Kontejnery adaptéru|> fronty, [ \<](queue.md) [ >zásobníku\<](stack.md)|
|[Zpracování chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)|výjimka > [, stdexcept>\<](stdexcept.md), [ system_error\<>](system-error.md) [ \<](exception.md)|
|[I/O a formátování](../cpp/string-and-i-o-formatting-modern-cpp.md)|[ \<](iomanip.md) [ \<](iosfwd.md) [ \<](fstream.md) [ \<](ios.md) [ \<](iostream.md)> systému souborů, fstream – >, iomanip >, iOS >, iosfwd >, iostream – >, [ \<](filesystem.md) [ IStream\<>](istream.md), [ ostream>,sstream>,streambuf>,strstream>\<](ostream.md) [ \<](sstream.md) [ \<](streambuf.md) [ \<](strstream.md)|
|Iterátory|[\<iterator>](iterator.md)|
|Lokalizace|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Matematické a číselné znaky|[ komplexní\<>](complex.md), [ omezení>,číselná>,náhodný>,poměr>,valarray>\<](limits.md) [ \<](numeric.md) [ \<](random.md) [ \<](ratio.md) [ \<](valarray.md)|
|[Správa paměti](../cpp/smart-pointers-modern-cpp.md)|přidělování > [, >\<paměti](memory.md), [ nového>,>\<](new.md) [ \<](allocators-header.md) [ \<](scoped-allocator.md)|
|Multithreading|[ \<](mutex.md) [ \<](shared-mutex.md)atomická > [ ,\<condition_variable >](condition-variable.md), [ \<budoucí >](future.md), mutex >, shared_mutex >, vlákno [ \<](atomic.md) [ \< >](thread.md)|
|Další nástroje|[ bitset\<>](bitset.md), [ Chrono>,funkční>,initializer_list>,řazenékolekcečlenů>,type_traits\<](chrono.md) [ \<](functional.md) [ \<](initializer-list.md) [ \<](tuple.md) [ \< >](type-traits.md) [ ,\<TypeInfo >](typeinfo.md), [ \<typeindex >](typeindex.md), [ \<Nástroj >](utility.md)|
|Řetězce a znaková data|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Viz také:

[Použití C++ hlaviček knihovny](using-cpp-library-headers.md)\
[C++Standardní knihovna](cpp-standard-library-reference.md)
