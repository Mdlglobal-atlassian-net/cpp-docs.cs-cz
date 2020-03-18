---
title: 'Unicode: široká charakterová sada'
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 3a0c5698544c72e19feea8f35b7f5a516d95d561
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444497"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: široká charakterová sada

Velký znak je 2 bajt kódu vícejazyčného znaku. Libovolný znak používaný v moderních computingech po celém světě, včetně technických symbolů a speciálních publikačních znaků, může být reprezentován specifikací Unicode jako širší znak. Vyvinutá a udržovaná velkým konsorciem, která zahrnuje Microsoft, je teď Standard Unicode široce přijatý.

Velký znak je typu **wchar_t**. Řetězec s velkým znakem je reprezentován jako pole **wchar_t []** a ukazuje na ukazatel `wchar_t*`. Můžete vyjádřit libovolný znak ASCII jako libovolný znak tím, že zadáte předponu písmene **L** znaku. Například L ' \ 0 ' je ukončující (16bitový) znak null. Podobně můžete vyjádřit libovolný řetězcový literál ASCII jako textový literál s velkým znakem jednoduše pomocí předpony písmena L až k literálu ASCII (L "Hello").

Obecně velké znaky zabírají více místa v paměti než vícebajtové znaky, ale rychleji se zpracovávají. Kromě toho lze reprezentovat pouze jedno národní prostředí v době v vícebajtovém kódování, zatímco všechny znakové sady na světě jsou zastoupeny současně reprezentacemi Unicode.

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
