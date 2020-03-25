---
title: Vyhrazená slova
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 16caacb77e052eebc8e2cd101990ee373535bd6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171148"
---
# <a name="reserved-words"></a>Vyhrazená slova

Následující slova jsou vyhrazena linkeru. Tyto názvy lze použít jako argumenty v [příkazech definice modulů](module-definition-dot-def-files.md) pouze v případě, že je název uzavřen v uvozovkách ("").

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**PŘEDNAČTENÍ**|
|**ZÁKLAD**|**IOPL**|**HLÁŠEN**|
|**ZNAKOVOU**|**Knihovna**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**VYHOVUJÍCÍ**|**LOADONCALL**<sup>1</sup>|**Čistá**<sup>1</sup>|
|**ÚDAJŮ**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**NÁZEV**|**Pohyblivý**<sup>1</sup>|**READWRITE**|
|**DEV386**|**Mobilní**,<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**Vypuštění**|**NĚKOLIKRÁT**|**OBČAN**|
|**DYNAMICKÉ**|**Jméno**|**Rezident**<sup>1</sup>|
|**POUZE PRO SPUŠTĚNÍ**|**NEWFILES**<sup>2</sup>|**ŘEZŮ**|
|**EXECUTEONLY**|**Data**<sup>1</sup>|**JEDNOTLIVÝCH**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**SDÍLENÉHO**|
|**EXETYPE**|**NONAME**|**KONKRÉTNÍ**|
|**EXPORTY**|**Neshoda**<sup>1</sup>|**VELIKOST ZÁSOBNÍKU**|
|**Opraveno**<sup>1</sup>|**Nelze odstranit**|**ZÁSTUPNÁ PROCEDURA**|
|**Funkce**<sup>2</sup>|**NTATO**|**ZNĚNÍ**|
|**VELIKOST HALDY**|**NESDÍLENÝCH**|**WINDOWAPI**|
|**OBJEM**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**Nečistý**<sup>1</sup>|**OBJEKTY**|**SYSTÉMU**|
|**Zahrnout**<sup>2</sup>|**Starý**<sup>1</sup>||

<sup>1</sup> linker vygeneruje upozornění ("ignorováno"), když dojde k tomuto termínu. Toto slovo je však stále rezervované.

<sup>2</sup> linker toto slovo ignoruje, ale neposílá žádné upozornění.

## <a name="see-also"></a>Viz také

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti linkeru MSVC](linker-options.md)
