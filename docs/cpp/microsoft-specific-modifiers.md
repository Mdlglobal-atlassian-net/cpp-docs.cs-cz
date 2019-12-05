---
title: Modifikátory specifické pro společnost Microsoft
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: 2d65c0fe99895949d537ccf4368df2add3ff91ad
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857421"
---
# <a name="microsoft-specific-modifiers"></a>Modifikátory specifické pro společnost Microsoft

Tato část popisuje rozšíření specifické pro společnost Microsoft pro jazyk C++ v následujících oblastech:

- [Založený na adresách](based-addressing.md), postupy použití ukazatele jako základu, ze kterého mohou být posunuty jiné ukazatele

- [Konvence volání funkce](calling-conventions.md)

- Rozšířené atributy třídy úložiště deklarované s klíčovým slovem [__declspec](declspec.md)

- Klíčové slovo [__w64](w64.md)

## <a name="microsoft-specific-keywords"></a>klíčová slova specifická pro společnost Microsoft

Mnoho klíčových slov specifických pro společnost Microsoft umožňuje změnit deklarace odvozených typů formulářů. Další informace o deklarátory najdete v tématu [deklarátory](overview-of-declarators.md).

|Klíčové slovo|Význam|Použít k vytvoření odvozených typů?|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|Název, který následuje, deklaruje 32bitový posun na 32bitovém základě obsaženém v prohlášení.|Ano|
|[__cdecl](cdecl.md)|Název, který následuje, používá pojmenování a konvence volání jazyka C.|Ano|
|[__declspec](declspec.md)|Název, který následuje, určuje atribut třídy úložiště společnosti Microsoft.|Ne|
|[__fastcall](fastcall.md)|Název, který následuje, deklaruje funkci, která používá registry (jsou-li k dispozici), namísto zásobníku pro předání argumentu.|Ano|
|[__restrict](extension-restrict.md)|Podobně jako __declspec ([omezit](restrict.md)), ale pro použití v proměnných.|Ne|
|[__stdcall](stdcall.md)|Název, který následuje, určuje funkci, která dodržuje standardní konvence volání.|Ano|
|[__w64](w64.md)|Označuje typ dat jako větší u 64bitového kompilátoru.|Ne|
|[__unaligned](unaligned.md)|Určuje, že ukazatel na typ nebo jiná data nejsou správně zarovnána.|Ne|
|[__vectorcall](vectorcall.md)|Název, který následuje, deklaruje funkci, která používá registry, včetně registrů SSE (jsou-li k dispozici), namísto zásobníku pro předání argumentu.|Ano|

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](cpp-language-reference.md)
