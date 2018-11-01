---
title: Změny v podpůrné funkci knihovny DLL s odloženým načtením od aplikace Visual C++ verze 6.0
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 8d50962bf66e07d6238be4a1a973c9d9ff06a556
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613769"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Změny v podpůrné funkci knihovny DLL s odloženým načtením od aplikace Visual C++ verze 6.0

Pokud máte více verzí jazyka Visual C++ v počítači nebo pokud jste definovali vlastní pomocné funkce, které mohou být ovlivněny změny provedené na knihovnu DLL funkci s odloženým načtením pomocné rutiny. Příklad:

- **__delayloadhelper –** je nyní **__delayloadhelper2 –**

- **__pfnDliNotifyHook** je nyní **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** je nyní **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL** je nyní **__FUnloadDelayLoadedDLL2**

> [!NOTE]
>  Pokud používáte výchozí pomocná funkce, neovlivní tyto změny vám. Neexistují žádné změny týkající se způsobu vyvolání linkeru.

## <a name="multiple-versions-of-visual-c"></a>Více verzí jazyka Visual C++

Pokud máte více verzí jazyka Visual C++ v počítači, ujistěte se, že má linker odpovídá delayimp.lib. Pokud dojde k neshodě, zobrazí se chyba linkeru, buď reporting `___delayLoadHelper2@8` nebo `___delayLoadHelper@8` jako nerozpoznaný externí symbol. Předchozí zahrnuje nové linkeru spuštěného s původní delayimp.lib a ten starý linkeru spuštěného s novou delayimp.lib znamená.

Pokud dojde k chybě nevyřešené linkeru, spusťte [dumpbin /linkermember](../../build/reference/linkermember.md): 1 na delayimp.lib, který očekáváte, že obsahují pomocnou funkci zobrazíte, které pomocná funkce je definována místo. Pomocná funkce mohou být také definovány v souboru objektů; Spustit [dumpbin /symbols](../../build/reference/symbols.md) a hledejte `delayLoadHelper(2)`.

Pokud víte, že máte linker Visual C++ 6.0, pak:

- Spusťte dumpbin pomocné rutiny zatížení zpoždění LIB nebo .obj soubor k určení, zda definuje **__delayloadhelper2 –**. Pokud ne, propojení se nezdaří.

- Definování **__delayloadhelper –** v zpoždění načíst soubor .lib nebo .obj pomocné rutiny.

## <a name="user-defined-helper-function"></a>Uživatelem definované pomocné funkce

Je-li definovány vlastní pomocné funkce a používáte aktuální verzi jazyka Visual C++, postupujte takto:

- Přejmenovat pomocnou funkci pro **__delayloadhelper2 –**.

- Protože ukazatele v popisovači zpoždění (v delayimp.h ImgDelayDescr) byly změněny z absolutních adresách (pro vozidla) na relativní adresy (RVA) fungovat podle očekávání v obě 32bitové a 64bitové aplikace, musíte převést tyto zpět na ukazatele. Byly zavedeny nové funkce: pfromrva –, který je součástí delayhlp.cpp. Tuto funkci můžete použít na všech polí v popisovači převést zpět na buď ukazatele 32 nebo 64 bitů. Pomocná funkce výchozí zpoždění zatížení nadále funkční šablonu, která slouží jako příklad.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Načtení všech importů pro knihovnu DLL se zpožděným načtením

Propojovací program můžete načíst všechny importy z knihovny DLL, který jste zadali jako zpožděné načtení. Zobrazit [načtení všech importů pro knihovnu DLL Delay-Loaded](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md) Další informace.

## <a name="see-also"></a>Viz také

[Základní informace o podpůrné funkci](understanding-the-helper-function.md)