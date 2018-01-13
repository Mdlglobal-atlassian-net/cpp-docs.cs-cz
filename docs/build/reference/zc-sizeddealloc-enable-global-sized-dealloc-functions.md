---
title: "/Zc:sizedDealloc (Povolit globální velikosti navrácení funkce) | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1343c037f87aee609de2b082cb87f7f1f2832221
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc:sizedDealloc (Povolit globální velikosti navrácení funkce)  
`/Zc:sizedDealloc` – Možnost kompilátoru říká kompilátoru přednostně volat globální `operator delete` nebo `operator delete[]` funkce, které mají druhý parametr typu `size_t` Pokud velikost objektu není k dispozici. Může použít tyto funkce `size_t` parametr za účelem optimalizace výkonu deallocator.   
  
## <a name="syntax"></a>Syntaxe  
`/Zc:sizedDealloc`[`-`\]  
  
## <a name="remarks"></a>Poznámky  
  
V C ++ 11 standard, může definovat statické členské funkce `operator delete` a `operator delete[]` které přebírají druhý, `size_t` parametr. Obvykle se používá v kombinaci s [new – operátor](../../cpp/new-operator-cpp.md) funkce pro implementaci efektivnější alokátorů a deallocators pro objekt. Ale C ++ 11 nedefinuje ekvivalentní sadu funkcí navrácení v globálním oboru. V C ++ 11, globální navrácení funkce, které mají druhý parametr typu `size_t` jsou považovány za funkce odstranění umístění. Se musí být explicitně volána předáním argumentem velikosti.  
  
C ++ 14 standardní mění chování kompilátoru. Když definujete globální `operator delete` a `operator delete[]` které přebírají druhý parametr typu `size_t`, kompilátor upřednostní na tyto funkce volat, když nejsou vyvolána člen oboru verze a velikost objektu je k dispozici. Kompilátor předá argument velikost implicitně. Jeden argument verze jsou volány při kompilátor nelze určit velikost objektu navrácena. Obvyklá pravidla pro výběr verze funkce navrácení k vyvolání, jinak hodnota pořád platit. Volání funkcí globální může explicitně určen předponou operátor řešení rozsahu (`::`) k volání funkce navrácení.  
  
Ve výchozím nastavení Visual C++ v sadě Visual Studio 2015 spouštění implementuje toto C ++ 14 standardní chování. Můžete to explicitně určit nastavením `/Zc:sizedDealloc` – možnost kompilátoru. Reprezentuje potenciálně nejnovější změny. Použít `/Zc:sizedDealloc-` možnost zachování staré chování, například když váš kód definuje operátory odstranit umístění, které používají druhý parametr typu `size_t`. Výchozí implementace knihovny sady Visual Studio globální navrácení funkce, které mají druhý parametr typu `size_t` vyvolání verze jeden parametr. Pokud váš kód poskytuje pouze jedním parametr globální delete – operátor and – operátor odstranit [], výchozí implementace knihovny funkcí globální velikostí navrácení vyvolání globální funkce.  
  
Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).  
  
## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
2.  Z **konfigurace** rozevírací nabídce, zvolte **všechny konfigurace**.  
3.  Vyberte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** stránku vlastností.  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala `/Zc:sizedDealloc` nebo `/Zc:sizedDealloc-` a potom zvolte **OK**.  
  
## <a name="see-also"></a>Viz také  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
[/Zc (shoda)](../../build/reference/zc-conformance.md)  
