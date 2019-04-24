---
title: Klíčová slova jazyka C
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: e1364e0edacd94efa4ade6c6892a57d619635a39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326791"
---
# <a name="c-keywords"></a>Klíčová slova jazyka C

„Klíčová slova“ jsou slova, která mají pro kompilátor jazyka C zvláštní význam. Ve fázích překladu 7 a 8 nemůže mít identifikátor stejné pořadí a velikost písmen jako klíčové slovo jazyka C. (Viz popis [fází překladu](../preprocessor/phases-of-translation.md) v *odkazu preprocesoru*; informace o identifikátorech naleznete v části [identifikátory](../c-language/c-identifiers.md).) Jazyk C používá následující klíčová slova:

|||||
|-|-|-|-|
|**auto**|**double**|**int**|**struct**|
|**break**|**else**|**long**|**switch**|
|**case**|**enum**|**register**|**Definice TypeDef**|
|**char**|**extern**|**return**|**sjednocení**|
|**const**|**float**|**short**|**bez znaménka**|
|**continue**|**for**|**podepsané**|**void**|
|**default**|**goto**|**sizeof**|**volatile**|
|**do**|**if**|**static**|**while**|

Klíčová slova nelze předefinovat. Ale můžete zadat text, který klíčová slova před kompilací nahradí pomocí jazyka C [direktivy preprocesoru](../preprocessor/preprocessor-directives.md).

**Microsoft Specific**

Standard ANSI C umožňuje vyhrazení identifikátorů začínajících dvěma podtržítky pro implementace kompilátoru. Konvence společnosti Microsoft tedy určuje, že názvy klíčových slov specifických pro společnost Microsoft jsou předcházeny dvěma podtržítky. Tato slova nelze použít jako názvy identifikátorů. Popis ANSI pravidla pro pojmenovávání identifikátorů včetně užití dvou podtržítek, najdete v části [identifikátory](../c-language/c-identifiers.md).

Kompilátor jazyka C společnosti Microsoft rozlišuje následující klíčová slova a speciální identifikátory:

|||||
|-|-|-|-|
|**__asm**<sup>3</sup>|**dllimport**<sup>2</sup>|**__int8**<sup>3</sup>|**naked**<sup>2</sup>|
|**__based –**<sup>1, 3</sup>|**__except**<sup>3</sup>|**__int16**<sup>3</sup>|**__stdcall**<sup>3</sup>|
|**__cdecl**<sup>3</sup>|**__fastcall**|**__int32**<sup>3</sup>|**vlákno**<sup>2</sup>|
|**__declspec**<sup>3</sup>|**__finally**<sup>3</sup>|**__int64**<sup>3</sup>|**__try**<sup>3</sup>|
|**dllexport**<sup>2</sup>|**__inline**<sup>3</sup>|**__leave**<sup>3</sup>||

<sup>1</sup> **__based** – klíčové slovo má omezené využití pro 32bitové a 64bitové cílové soubory.

<sup>2</sup> jde o speciální identifikátory při použití s **__declspec**; jejich použití v jiných kontextech není omezeno.

<sup>3</sup> z důvodu kompatibility s předchozími verzemi, tato klíčová slova jsou dostupné s dvěma úvodními podtržítky a jedno vedoucí podtržítko, když jsou povolena rozšíření společnosti Microsoft.

Ve výchozím nastavení jsou povolena rozšíření společnosti Microsoft. Zajistit, že plné přenositelnosti programů lze zakázat rozšíření Microsoft zadáním [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) možnost během kompilace. Když toto provedete, jsou zakázána klíčová slova specifická pro společnost Microsoft.

Jsou-li rozšíření společnosti Microsoft povolena, lze klíčová slova specifická pro společnost Microsoft uvedená výše používat v programech. Kvůli souladu s normou ANSI začíná většina těchto klíčových slov dvojitým podtržítkem. Čtyři výjimky, **dllexport**, **dllimport**, **naked**, a **vlákno**, jsou používány pouze s **__declspec** a proto nevyžadují dvě podtržítka na začátku. Z důvodu zpětné kompatibility jsou podporovány verze ostatních klíčových slov s jedním podtržítkem.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Elementy jazyka C](../c-language/elements-of-c.md)
