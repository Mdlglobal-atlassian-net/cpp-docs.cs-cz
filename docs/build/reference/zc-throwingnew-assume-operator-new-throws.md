---
title: "/Zc:throwingNew (Assume operátor nové vyvolává) | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- throwingNew
- /Zc:throwingNew
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bc784af1c23576ff68c8be8b4b400cd10cc8b0e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (Assume operátor nové vyvolává)  
Když `/Zc:throwingNew` je zadána možnost, kompilátor optimalizuje volání `operator new` tak, aby přeskočil kontroluje návratový ukazatel s hodnotou null. Tato možnost určuje kompilátor předpokládají, že všechny propojené implementace `operator new` a vlastní alokátorů odpovídat C++ standard a throw na došlo k chybě přidělení. Ve výchozím nastavení v sadě Visual Studio, kompilátor pessimistically generuje kontroly hodnoty null (`/Zc:throwingNew-`) pro toto volání, protože uživatele můžete propojit s na jiný vyvolávání implementace `operator new` nebo napište vlastní allocator rutiny, které vracejí ukazatelé s hodnotou null.  
  
## <a name="syntax"></a>Syntaxe  
  
`/Zc:throwingNew`[`-`]  
  
## <a name="remarks"></a>Poznámky  
  
Od ISO C ++ 98, má zadanou standardní, výchozí [new – operátor](../../standard-library/new-operators.md#op_new) vyvolá `std::bad_alloc` když dojde k selhání přidělení paměti. Verzí aplikace Visual C++ na Visual Studio 6.0 vrátil hodnotu null. ukazatel na došlo k chybě přidělení. Od verze Visual Studio 2002 `operator new` vyhovuje standardní a vyvolá při selhání. Pro podporu kód, který používá starší styl přidělení, Visual Studio poskytuje korelovat implementaci `operator new` v *nothrownew.obj* ukazatele null, vrátí při selhání. Ve výchozím nastavení kompilátor také generuje Obranným kontroly hodnoty null zabránit tyto starší stylu alokátorů způsobí okamžité havárií při selhání. `/Zc:throwingNew` Říká kompilátoru, vynechte tyto kontroly hodnoty null, za předpokladu, že všechny propojené paměti alokátorů odpovídají standardní. To neplatí explicitní bez vyvolávání `operator new` přetížení, které jsou deklarovány s použitím další parametr typu `std::nothrow_t` a používat explicitní `noexcept` specifikace.  
  
Koncepčně, pro vytvoření objektu v úložišti volné, kompilátor generuje kód do přidělit jeho paměť a potom k vyvolání jeho konstruktoru inicializovat paměť. Protože – kompilátor Visual C++ za normálních okolností nemůže určit Pokud tento kód propojí nonkonformní, vyvolání allocator, ve výchozím nastavení také vytváří kontrolu hodnotu null. před voláním konstruktoru. Zabrání se tak ukazatele null dereference ve volání konstruktoru, pokud se nezdaří přidělení není aktivována. Ve většině případů tyto kontroly nejsou potřebné, protože výchozí `operator new` alokátorů throw místo vrácení ukazatelé s hodnotou null. Kontroly mít také velice nepříjemná vedlejší účinky. Jejich nafouknutí velikosti kódu, jejich vyplnění předpověď větve a jejich bránit jiné optimalizace kompilátoru užitečné například devirtualization nebo const šíření inicializovaný objekt. Kontroly existovat jenom pro podporu kód, který odkazuje na *nothrownew.obj* nebo má vlastní nonkonformní `operator new` implementace. Pokud nepoužijete nonkonformní `operator new`, doporučujeme použít `/Zc:throwingNew` optimalizaci kódu.  
  
Pokud zkompilujete pomocí generování kódu v době propojování (LTCG), není potřeba zadat `/Zc:throwingNew`. Pokud je kód zkompilován pomocí LTCG, můžete kompilátor zjistí, jestli výchozí, který odpovídá `operator new` implementace slouží. Pokud ano, kompilátor automaticky vynechány kontroly hodnoty null. Hledá linkeru `/ThrowingNew` příznak říct Pokud implementace `operator new` shoduje. Můžete zadat Tento příznak, který linkeru včetně tato direktiva ve zdroji týkající se vaší implementace nové vlastní operátor:  
  
```cpp  
#pragma comment(linker, "/ThrowingNew")  
```  
  
Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).  
  
## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
2.  Z **konfigurace** rozevírací nabídce, zvolte **všechny konfigurace**.  
3.  Vyberte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** stránku vlastností.  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala `/Zc:throwingNew` nebo `/Zc:throwingNew-` a potom zvolte **OK**.  
  
## <a name="see-also"></a>Viz také  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
[/Zc (shoda)](../../build/reference/zc-conformance.md)  
[noexcept (C++)](../../cpp/noexcept-cpp.md)  
[Specifikace výjimek (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)  
[ukončit (výjimek)](../../standard-library/exception-functions.md#terminate)  