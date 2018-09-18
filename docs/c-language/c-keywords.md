---
title: Klíčová slova jazyka C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3091437333d01db3fa556cb3c164e916c3628333
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057790"
---
# <a name="c-keywords"></a>Klíčová slova jazyka C

„Klíčová slova“ jsou slova, která mají pro kompilátor jazyka C zvláštní význam. Ve fázích překladu 7 a 8 nemůže mít identifikátor stejné pořadí a velikost písmen jako klíčové slovo jazyka C. (Viz popis [fází překladu](../preprocessor/phases-of-translation.md) v *odkazu preprocesoru*; informace o identifikátorech naleznete v části [identifikátory](../c-language/c-identifiers.md).) Jazyk C používá následující klíčová slova:

|||||
|-|-|-|-|
|**auto**|**double**|**int**|**struct**|
|**break**|**else**|**long**|**switch**|
|**případ**|**enum**|**Registrace**|**Definice TypeDef**|
|**char**|**extern**|**return**|**sjednocení**|
|**const**|**float**|**short**|**bez znaménka**|
|**continue**|**for**|**podepsané**|**void**|
|**default**|**goto**|**sizeof**|**volatile**|
|**do**|**if**|**static**|**while**|

Klíčová slova nelze předefinovat. Ale můžete zadat text, který klíčová slova před kompilací nahradí pomocí jazyka C [direktivy preprocesoru](../preprocessor/preprocessor-directives.md).

**Specifické pro Microsoft**

Standard ANSI C umožňuje vyhrazení identifikátorů začínajících dvěma podtržítky pro implementace kompilátoru. Konvence společnosti Microsoft tedy určuje, že názvy klíčových slov specifických pro společnost Microsoft jsou předcházeny dvěma podtržítky. Tato slova nelze použít jako názvy identifikátorů. Popis ANSI pravidla pro pojmenovávání identifikátorů včetně užití dvou podtržítek, najdete v části [identifikátory](../c-language/c-identifiers.md).

Kompilátor jazyka C společnosti Microsoft rozlišuje následující klíčová slova a speciální identifikátory:

|||||
|-|-|-|-|
|**__asm**|**DllImport**2|**__int8**|**naked**2|
|**__based –** 1|**__except**|**__int16**|**__stdcall**|
|**__cdecl**|**__fastcall**|**__int32**|**vlákno**2|
|**__declspec**|**__finally**|**__int64**|**__try**|
|**dllexport**2|**__inline**|**__leave**||

1. **__Based** – klíčové slovo má omezené využití pro 32bitové a 64bitové cílové soubory.

2. Toto jsou speciální identifikátory při použití s **__declspec**; jejich použití v jiných kontextech není omezeno.

Ve výchozím nastavení jsou povolena rozšíření společnosti Microsoft. K zajištění plné přenositelnosti programů lze zakázat rozšíření Microsoft zadáním možnosti kompilátoru /Za (kompilace z důvodu kompatibility ANSI) během kompilace. Když toto provedete, jsou zakázána klíčová slova specifická pro společnost Microsoft.

Jsou-li rozšíření společnosti Microsoft povolena, lze klíčová slova specifická pro společnost Microsoft uvedená výše používat v programech. Kvůli souladu s normou ANSI začíná většina těchto klíčových slov dvojitým podtržítkem. Čtyři výjimky, **dllexport**, **dllimport**, **naked**, a **vlákno**, jsou používány pouze s **__declspec** a proto nevyžadují dvě podtržítka na začátku. Z důvodu zpětné kompatibility jsou podporovány verze ostatních klíčových slov s jedním podtržítkem.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Elementy jazyka C](../c-language/elements-of-c.md)