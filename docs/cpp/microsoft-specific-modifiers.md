---
title: Modifikátory specifické pro společnost Microsoft | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/16/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b845ccb24d6d7a93767ec3c3219562c1c87bf81f
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820241"
---
# <a name="microsoft-specific-modifiers"></a>Modifikátory specifické pro společnost Microsoft

Tato část popisuje rozšíření specifické pro společnost Microsoft pro jazyk C++ v následujících oblastech:

- [Základní adresování](based-addressing.md), praxe používání ukazatele jako základ, ze kterého mohou být posouvány jiné ukazatele

- [Konvence volání funkce](calling-conventions.md)

- Rozšířené atributy tříd úložiště deklarované s [__declspec](declspec.md) – klíčové slovo

- [__W64](w64.md) – klíčové slovo

## <a name="microsoft-specific-keywords"></a>Klíčová slova specifická pro společnost Microsoft

Mnoho klíčových slov specifických pro společnost Microsoft umožňuje změnit deklarace odvozených typů formulářů. Další informace o deklarátorech naleznete v tématu [Deklarátory](overview-of-declarators.md).

|Klíčové slovo|Význam|Použít k vytvoření odvozených typů?|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|Název, který následuje, deklaruje 32bitový posun na 32bitovém základě obsaženém v prohlášení.|Ano|
|[__cdecl](cdecl.md)|Název, který následuje, používá pojmenování a konvence volání jazyka C.|Ano|
|[__declspec](declspec.md)|Název, který následuje, určuje atribut třídy úložiště specifické pro společnost Microsoft.|Ne|
|[__fastcall](fastcall.md)|Název, který následuje, deklaruje funkci, která používá registry, pokud je k dispozici, namísto zásobníku pro předání argumentu.|Ano|
|[__restrict](extension-restrict.md)|Podobně jako __declspec ([omezit](restrict.md)), ale pro použití u proměnné.|Ne|
|[__stdcall](stdcall.md)|Název, který následuje, určuje funkci, která dodržuje standardní konvence volání.|Ano|
|[__w64](w64.md)|Označuje typ dat jako větší u 64bitového kompilátoru.|Ne|
|[__unaligned](unaligned.md)|Určuje, že ukazatel na typ nebo jiná data nejsou zarovnána...|Ne|
|[__vectorcall](vectorcall.md)|Název, který následuje, deklaruje funkci, která používá registry, včetně registrů SSE, pokud je k dispozici, namísto zásobníku pro předání argumentu.|Ano|

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](cpp-language-reference.md)