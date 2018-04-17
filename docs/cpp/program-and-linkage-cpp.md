---
title: Program a propojení (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/09/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab24c552a150e5a14037d727c8d3428eb6bbf809
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="program-and-linkage--c"></a>Program a propojení (C++)

V programu C++ každý globální symbol lze definovat pouze jednou, i v případě, že program se skládá z několika jednotky překladu. Jednotky překladu se skládá z soubor implementace (sada, .hpp, .cxx atd.) a všechny hlavičky, které obsahuje přímo nebo nepřímo. Program se skládá z jedné nebo více propojených jednotek překladu. 

## <a name="linkage-vs-scope"></a>Propojení oproti oboru

Koncept *propojení* vztahuje se k viditelnost globální symboly (například, názvy typů názvy proměnných a funkce) v rámci programu jako celek jednotky překladu. Koncept *oboru* odkazuje na symboly, které jsou deklarované v rámci bloku například obor názvů, třídu nebo tělo funkce. Tyto symboly jsou viditelné pouze v rámci oboru, ve kterém jsou definovány; Koncept propojení se nevztahuje na ně.

## <a name="external-vs-internal-linkage"></a>Externí oproti vnitřní propojení

Globální proměnné non-const a bezplatné funkce ve výchozím nastavení mají externí propojení; jsou viditelné z jakékoli jednotky překladu v programu. Toto chování můžete přepsat pomocí výslovně deklarace je jako **statické** což omezuje jejich viditelnost na stejné překlad jednotku, ve které jsou deklarované. Tento význam **statické** se liší od její význam při použití místní proměnné. Proměnných deklarovaných jako **const** ve výchozím nastavení mají vnitřní propojení.

## <a name="extern-constexpr-linkage"></a>Extern constexpr propojení

V dřívějších verzích sady Visual Studio kompilátor vždy přiřadil constexpr proměnné vnitřní propojení i v případě, že proměnná byla označena jako externí. V aplikaci Visual Studio 2017 verze 15,5, nového přepínače kompilátoru (nebo Zc:externConstexpr) umožňuje správné chování podle standardů. Nakonec stane výchozí.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Pokud soubor hlaviček obsahuje proměnné deklarované extern constexpr, musí být označen **__declspec(selectany)** aby bylo možné správně používat jeho duplicitní deklarace kombinaci:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="see-also"></a>Viz také

 [Základní koncepty](../cpp/basic-concepts-cpp.md)