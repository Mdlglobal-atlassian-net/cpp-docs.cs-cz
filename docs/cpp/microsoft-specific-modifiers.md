---
title: Modifikátory specifické pro společnost Microsoft
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: 119e4d06d0235bbf637eefe8754668d3e90b0c52
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301783"
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

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](cpp-language-reference.md)
