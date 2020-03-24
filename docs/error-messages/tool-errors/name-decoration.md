---
title: Dekorování názvů
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: cc00c971eac2a089ccec5bd9eab594bdf4e8348e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173514"
---
# <a name="name-decoration"></a>Dekorování názvů

Dekorace názvů obvykle odkazuje C++ na konvence pojmenování, ale může se vztahovat i na několik případů jazyka C. Ve výchozím nastavení C++ používá název funkce, parametry a návratový typ k vytvoření názvu linkeru pro funkci. Zvažte následující deklaraci funkce:

`void CALLTYPE test(void);`

V následující tabulce je uveden název linkeru pro různé konvence volání.

|Konvence volání|soubor `extern "C"` nebo `.c`|`.cpp`, `.cxx` nebo `/TP`|
|------------------------|---------------------------|------------------------|
|Konvence vytváření názvů v jazyce C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Rychlé konvence pojmenování volání (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Standardní konvence pojmenování volání (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Konvence pojmenování volání vektoru (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Použijte `extern "C"` pro volání funkce jazyka C z C++. `extern "C"` vynutí použití konvence pojmenování v jazyce C C++ pro funkce, které nejsou třídy. Upozorňujeme na přepínače kompilátoru **/TC** nebo **/TP**, které instruují, že kompilátor bude ignorovat příponu filename a zkompilovat soubor jako C nebo C++v uvedeném pořadí. Tyto možnosti mohou způsobit názvy linkerů, které neočekáváte.

Tato chyba může způsobovat i prototypy funkcí, které mají neshodné parametry. Dekorace názvů zahrnuje parametry funkce do konečného názvu dekorované funkce. Volání funkce s typy parametrů, které se neshodují v deklaraci funkce, může také způsobit LINKERŮ LNK2001.

V současné době nejsou k dispozici žádné standardy pro C++ pojmenování mezi dodavateli kompilátoru nebo dokonce mezi různými verzemi kompilátoru. Propojování souborů objektů zkompilovaných jinými kompilátory nemusí mít stejné schéma pojmenování a může způsobit nevyřešené externí objekty.

## <a name="see-also"></a>Viz také

[Chyba linkerů LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
