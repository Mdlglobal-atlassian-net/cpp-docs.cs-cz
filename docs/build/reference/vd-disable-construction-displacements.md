---
title: "-vd (zakázat posunutí konstrukcí) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /vd
dev_langs: C++
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b945c4a3191554d5299522ff376772d6362a616c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vd-disable-construction-displacements"></a>/vd (Zakázat posunutí konstrukcí)
## <a name="syntax"></a>Syntaxe  
  
```  
/vdn  
```  
  
## <a name="arguments"></a>Arguments  
 `0`  
 Potlačí vtordisp – konstruktor/destruktor přestavění člena. Vyberte tuto možnost, pouze pokud jste si jisti, že všechny třídy konstruktory a destruktory volání virtuální funkce prakticky.  
  
 `1`  
 Umožňuje vytvoření skrytá vtordisp – konstruktor/destruktor přestavění členů. Tato volba je výchozí.  
  
 `2`  
 Umožňuje používat [dynamic_cast – operátor](../../cpp/dynamic-cast-operator.md) vytvářen objektu. Například dynamic_cast z virtuální základní třídy odvozené třídy.  
  
 **/vd2** přidá pole vtordisp – Pokud máte virtuální základní s virtuální funkce. **/ vd1** by mělo být dostatečné. Nejběžnější případ kde **/vd2** je nutné je po pouze virtuální funkce v virtuální základní destruktor.  
  
## <a name="remarks"></a>Poznámky  
 Tyto možnosti platí pouze pro C++ kód, který používá virtuální základny.  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]implementuje podporu přestavění konstrukce C++ v situacích, kdy je použít virtuální dědičnost. Posunutí konstrukcí vytvoří, když virtuální funkce deklarován v virtuální základní a přepsání v odvozené třídě problém vyřešit, je volána z konstruktoru během vytváření další odvozené třídy.  
  
 Problém je, že virtuální funkce může být předána nesprávné `this` ukazatele v důsledku rozporů mezi posunutí pro virtuální základny třídu a posunutí k jejich odvozené třídy. Řešení poskytuje jeden konstrukce přestavění úpravu, názvem vtordisp pole pro každý virtuální základní třídy.  
  
 Ve výchozím nastavení pole vtordisp vydávají vždy, když kód definuje uživatelské konstruktory a destruktory a také přepsání virtuální funkce virtuální základny.  
  
 Tyto možnosti ovlivní celou zdrojové soubory. Použití [vtordisp](../../preprocessor/vtordisp.md) potlačit a pak znovu povolte pole vtordisp na základě třídy třídy.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)