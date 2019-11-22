---
title: C++standardní soubory hlaviček knihovny
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 807e65c69e55d8790b77a493e4ae1878aa740557
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305405"
---
# <a name="c-standard-library-header-files"></a>C++standardní soubory hlaviček knihovny

Hlavičkové soubory pro C++ standardní knihovnu a rozšíření podle kategorie.

## <a name="headers-by-category"></a>Záhlaví podle kategorie

::: moniker range=">=vs-2017"

| Kategorie | záhlaví |
| - | - |
| [Algoritmy](../cpp/algorithms-modern-cpp.md) | [\<algoritmu >](algorithm.md) [\<cstdlib >](cstdlib.md) [\<číselné >](numeric.md) |
| Atomické operace |  [\<atomická >](atomic.md)<sup>11</sup> |
| Obálky knihovny C | [\<cassert >](cassert.md), [\<ccomplex >](ccomplex.md)<sup>11 a b</sup>, [\<cctype >](cctype.md), [\<cerrno >](cerrno.md), [\<cfenv >](cfenv.md)<sup>11</sup>, [\<cfloat >](cfloat.md), [\<cinttypes >](cinttypes.md)<sup>11</sup>, [\<ciso646 >](ciso646.md)<sup>b</sup>, [\<climits >](climits.md), [\<clocale](clocale.md) [>,\<cmath >,\<](cmath.md) [csetjmp >,\<](csetjmp.md) [ csignal >](csignal.md), [\<cstdalign >](cstdalign.md)<sup>11 a b</sup> [\<cstdarg >](cstdarg.md), [\<cstdbool >](cstdbool.md)<sup>11 a b</sup>, [\<cstddef >](cstddef.md), [\<cstdint >](cstdint.md)<sup>11</sup>, [\<cstdio >](cstdio.md), [\<cstdlib >](cstdlib.md), [\<CString >](cstring.md),\<ctgmath [>](ctgmath.md)<sup>11 a b</sup>, [\<CTime – >](ctime.md),\<[cuchar >](cuchar.md)<sup>11</sup> , [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md) |
| Koncepty | \<koncepty ><sup>20</sup> |
| [Kontejnery](../cpp/containers-modern-cpp.md) | |
| Kontejnery sekvence | [\<array >](array.md)<sup>11</sup>, [\<deque >](deque.md), [\<forward_list >](forward-list.md)<sup>11</sup>, [\<seznam >](list.md), [\<Vector >](vector.md) |
| Seřazené asociativní kontejnery| [\<map>](map.md), [\<set>](set.md) |
| Neuspořádané asociativní kontejnery | [\<unordered_map >](unordered-map.md)<sup>11</sup> [\<unordered_set >](unordered-set.md)<sup>11</sup> |
| Adaptéry kontejneru | [>\<fronty](queue.md) [\<zásobníku >](stack.md) |
| Zobrazení kontejneru | \<rozpětí ><sup>20</sup> |
| [Zpracování chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert >](cassert.md), [\<> výjimky](exception.md) [\<stdexcept >](stdexcept.md), [\<system_error >](system-error.md)<sup>11</sup> |
| Obecné nástroje | \<jakýchkoli ><sup>17</sup>, [\<bitset >](bitset.md), \<charconv ><sup>17</sup>, [\<cstdlib >](cstdlib.md), \<spouštění ><sup>17</sup>, [\<funkční >](functional.md), [\<paměti >](memory.md), \<memory_resource ><sup>17</sup>, \<volitelné ><sup>17</sup>,\<[poměr >](ratio.md)<sup>11</sup>, [\<scoped_allocator >](scoped-allocator.md)<sup>11</sup>, [\<řazené kolekce členů >](tuple.md)<sup>11</sup> [,\<type_traits >](type-traits.md)<sup>11</sup> [\<typeindex >](typeindex.md)<sup>11</sup>, [\<utility >](utility.md), \<varianta ><sup>17</sup> |
| [I/O a formátování](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes >](cinttypes.md)<sup>11</sup>, [\<cstdio >](cstdio.md), [\<systému souborů >](filesystem.md)<sup>17</sup>, [\<fstream – >](fstream.md), [\<iomanip >](iomanip.md), [\<ios >](ios.md), [\<iosfwd >](iosfwd.md), [\<iostream – >](iostream.md), [\<IStream >](istream.md), [\<ostream >](ostream.md),\<sstream [>](sstream.md), [\<streambuf >](streambuf.md), [\<](strstream.md)<sup>strstream > </sup>\<syncstream ><sup>20</sup> |
| Iterátory | [\<iterator>](iterator.md) |
| Podpora jazyků | [\<cfloat >](cfloat.md), [\<climits >](climits.md), [\<codecvt >](codecvt.md)<sup>11 a</sup>, \<porovnání ><sup>20</sup>, \<kontrakt ><sup>20</sup>, \<korutina<sup>> 20</sup>, [\<csetjmp >](csetjmp.md), [\<csignal >](csignal.md), [\<cstdarg >](cstdarg.md),\<[cstddef >](cstddef.md), [\<cstdint >](cstdint.md)<sup>11</sup> [,\<cstdlib >,](cstdlib.md)\<[výjimka >](exception.md) , [\<initializer_list >](initializer-list.md)<sup>11</sup> [\<omezení >](limits.md)\<> [nové\<](new.md), [> TypeInfo \<](typeinfo.md), > verze<sup>20</sup> |
| Lokalizace | [\<clocale >](clocale.md), [\<codecvt >](codecvt.md)<sup>11 a</sup>, [\<CVT/wbuffer >](cvt-wbuffer.md), [\<CVT/wstring >](cvt-wstring.md), [\<národním prostředí >](locale.md) |
| Matematické a číselné znaky | \<bit ><sup>20</sup>, [\<cfenv >](cfenv.md)<sup>11</sup>, [\<cmath >](cmath.md), [\<komplexní >](complex.md), [\<cstdlib >](cstdlib.md), [\<omezení >](limits.md), [\<číselná >](numeric.md), [\<náhodný >](random.md)<sup>11</sup>, [\<poměr >](ratio.md)<sup>11</sup>\<[> valarray](valarray.md) |
| [Správa paměti](../cpp/smart-pointers-modern-cpp.md) | [\<přidělování >](allocators-header.md), [\<> paměti](memory.md)\<memory_resource ><sup>17</sup>\<[nové >](new.md)\<scoped_allocator > [](scoped-allocator.md)<sup>11</sup> |
| Multithreading | [\<atomická >](atomic.md)<sup>11</sup> [\<condition_variable >](condition-variable.md)<sup>11</sup>, [\<budoucí >](future.md)<sup>11</sup>, [\<mutex >](mutex.md)<sup>11</sup>, [\<shared_mutex >](shared-mutex.md)<sup>14</sup>, [\<vlákno >](thread.md)<sup>11</sup> |
| Rozsahy | rozsahy \<><sup>20</sup> |
| Regulární výrazy | [\<regex >](regex.md)<sup>11</sup> |
| Řetězce a znaková data | [\<cctype >](cctype.md), [\<cstdlib >](cstdlib.md), [\<cstring >](cstring.md), [\<cuchar >](cuchar.md)<sup>11</sup>, [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md), [\<regulárního výrazu >](regex.md)<sup>11</sup>, [\<řetězec >](string.md), [\<string_view >](string-view.md)<sup>17</sup> |
| Čas | [\<chrono >](chrono.md)<sup>11</sup> [\<CTime – >](ctime.md) |

<sup>11</sup> přidáno ve standardu c++ 11. \
<sup>14</sup> přidáno ve standardu c++ 14. \
<sup>17</sup> přidáno ve standardu c++ 17. \
<sup>20</sup> přidáno v konceptu c++ 20 Standard. \
<sup>zastaralé ve</sup> standardu c++ 17. \
<sup>b</sup> odebrána v konceptu c++ 20 Standard. \
Jazyk <sup>c</sup> je zastaralý ve standardu c++ 98.

::: moniker-end

::: moniker range="vs-2015"

|Kategorie|záhlaví|
|-|-|
|[Algoritmy](../cpp/algorithms-modern-cpp.md)|[algoritmus \<>](algorithm.md)|
|Obálky knihovny C|[\<cassert >](cassert.md), [\<cctype >](cctype.md), [\<cerrno >](cerrno.md), [\<cfenv >](cfenv.md), [\<cfloat >](cfloat.md), [\<cinttypes >](cinttypes.md), [\<ciso646 >](ciso646.md), [\<climits >](climits.md), [\<clocale](clocale.md)>, [\<](cmath.md) [](cstdarg.md) [](csetjmp.md) [](csignal.md) [](cstdbool.md) [cmath >,\<csetjmp >,\<csignal >,\<cstdarg >,\<cstdbool >,\<cstddef >](cstddef.md), [\<cstdint >](cstdint.md), [\<cstdio >](cstdio.md), [\<cstdlib >](cstdlib.md), [\<CString >](cstring.md), [\<ctgmath >](ctgmath.md), [\<CTime – >](ctime.md), [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md)|
|[Kontejnery](../cpp/containers-modern-cpp.md)||
|Kontejnery sekvence|[\<> pole](array.md), [\<deque >](deque.md), [\<forward_list >](forward-list.md), [\<seznam >](list.md), [\<Vector >](vector.md)|
|Seřazené asociativní kontejnery| [\<map>](map.md), [\<set>](set.md)|
|Neuspořádané asociativní kontejnery|[\<unordered_map >](unordered-map.md) [\<unordered_set >](unordered-set.md)|
|Kontejnery adaptéru|[>\<fronty](queue.md) [\<zásobníku >](stack.md)|
|[Zpracování chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<> výjimky](exception.md) [\<stdexcept >](stdexcept.md) [\<](system-error.md) system_error >|
|[I/O a formátování](../text/string-and-i-o-formatting-modern-cpp.md)|[\<> systému souborů](filesystem.md) [\<fstream – >](fstream.md), [\<iomanip >](iomanip.md), [\<ios >](ios.md), [\<iosfwd >](iosfwd.md), [\<iostream – >](iostream.md), [\<istream >](istream.md), [\<ostream >](ostream.md), [\<sstream >](sstream.md), [\<streambuf >](streambuf.md),\<[strstream >](strstream.md)|
|Iterátory|[\<iterator>](iterator.md)|
|Lokalizace|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Matematické a číselné znaky|[\<složitých >](complex.md) [\<limity >](limits.md), [\<číselné >](numeric.md), [\<náhodný >](random.md), [\<poměr](ratio.md)>\<> [](valarray.md)|
|[Správa paměti](../cpp/smart-pointers-modern-cpp.md)|[\<přidělování >](allocators-header.md), [\<> paměti](memory.md) [\<nové >](new.md), [\<scoped_allocator >](scoped-allocator.md)|
|Multithreading|[\<atomická >](atomic.md), [\<condition_variable >](condition-variable.md), [\<budoucí >](future.md), [\<mutex >](mutex.md), [\<shared_mutex >](shared-mutex.md), [\<vlákna](thread.md) >|
|Další nástroje|[\<bitset >](bitset.md), [\<chrono >](chrono.md), [\<funkční >](functional.md), [\<initializer_list >](initializer-list.md), [\<řazené kolekce členů >](tuple.md), [\<type_traits >](type-traits.md), [\<TypeInfo >](typeinfo.md), [\<typeindex >](typeindex.md), [\<utility >](utility.md)|
|Řetězce a znaková data|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Viz také:

[Použití C++ hlaviček knihovny](using-cpp-library-headers.md)\
[C++Standardní knihovna](cpp-standard-library-reference.md)
