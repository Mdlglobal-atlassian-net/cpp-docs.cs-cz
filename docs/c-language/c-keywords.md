---
title: "Klíčová slova jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 71e5c715c6065e8c05466bc3f09eba57606b304e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-keywords"></a>Klíčová slova jazyka C
„Klíčová slova“ jsou slova, která mají pro kompilátor jazyka C zvláštní význam. Ve fázích překladu 7 a 8 nemůže mít identifikátor stejné pořadí a velikost písmen jako klíčové slovo jazyka C. (Viz popis [fáze překladu](../preprocessor/phases-of-translation.md) v *preprocesor odkaz*; informace o identifikátory, najdete v tématu [identifikátory](../c-language/c-identifiers.md).) Jazyk C používá následující klíčová slova:  
  
|||||  
|-|-|-|-|  
|**automaticky**|**Double**|**celá čísla**|**Struktura**|  
|**Konec**|**else**|**dlouhá**|**přepínače**|  
|**případ**|**výčet**|**Registrace**|**Definice TypeDef**|  
|**Char**|**extern**|**Vrátí**|**sjednocení**|  
|**Const**|**plovoucí desetinná čárka**|**krátký**|**bez znaménka**|  
|**pokračovat**|**pro**|**podepsané**|**void**|  
|**Výchozí**|**goto – příkaz**|**sizeof –**|**volatile**|  
|**proveďte**|**Pokud**|**statické**|**Při**|  
  
 Klíčová slova nelze předefinovat. Můžete však zadat text, který má být nahrazena klíčových slov před kompilace pomocí C [preprocesor – direktivy](../preprocessor/preprocessor-directives.md).  
  
 **Konkrétní Microsoft**  
  
 Standard ANSI C umožňuje vyhrazení identifikátorů začínajících dvěma podtržítky pro implementace kompilátoru. Konvence společnosti Microsoft tedy určuje, že názvy klíčových slov specifických pro společnost Microsoft jsou předcházeny dvěma podtržítky. Tato slova nelze použít jako názvy identifikátor. Popis ANSI pravidla pro pojmenovávání identifikátory, včetně použití dvojité podtržítka, najdete v části [identifikátory](../c-language/c-identifiers.md).  
  
 Kompilátor jazyka C společnosti Microsoft rozlišuje následující klíčová slova a speciální identifikátory:  
  
|||||  
|-|-|-|-|  
|**__asm**|**DllImport**2|**__int8**|**holé**2|  
|**__based –**1|**__except**|**__int16**|**__stdcall**|  
|**__cdecl**|**__fastcall**|**__int32**|**vlákno**2|  
|**__declspec**|**__finally**|**__int64**|**__try**|  
|**dllexport**2|**__inline**|**__leave**||  
  
 1. **__Based** – klíčové slovo má omezenou používá pro 32bitové a 64bitové verze cílového kompilace.  
  
 2. Toto jsou speciální identifikátory při použití s **__declspec**; jejich použití v jiných kontextech není omezen.  
  
 Rozšíření Microsoft jsou ve výchozím nastavení povolené. K zajištění plné přenositelnosti programů lze zakázat rozšíření Microsoft zadáním možnosti kompilátoru /Za (kompilace z důvodu kompatibility ANSI) během kompilace. Když to uděláte, jsou zakázané klíčová slova specifická pro společnost Microsoft.  
  
 Jsou-li rozšíření společnosti Microsoft povolena, lze klíčová slova specifická pro společnost Microsoft uvedená výše používat v programech. Kvůli souladu s normou ANSI začíná většina těchto klíčových slov dvojitým podtržítkem. Čtyři výjimky, **dllexport**, **dllimport**, **holé**, a **vlákno**, se používají pouze s **__declspec** a proto nevyžadují na začátku dvojité podtržítko. Z důvodu zpětné kompatibility jsou podporovány verze ostatních klíčových slov s jedním podtržítkem.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Elementy jazyka C](../c-language/elements-of-c.md)