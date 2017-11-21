---
title: "Závažná chyba C1189 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1189
dev_langs: C++
helpviewer_keywords: C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e8d3c9ff44a436688accfe267141390d23c0eb5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1189"></a>Závažná chyba C1189
\#Chyba: uživatelem dodaný chybová zpráva  
  
 Je generován C1189 `#error` – direktiva. Vývojáři, který kódy direktiva Určuje text chybové zprávy. Další informace najdete v tématu [#error – direktiva (C/C++)](../../preprocessor/hash-error-directive-c-cpp.md).  
  
 Následující ukázka generuje C1189. V ukázce vývojář problémy vlastní chybové zprávy, protože `_WIN32` identifikátor není definován:  
  
```  
// C1189.cpp  
#undef _WIN32  
#if !defined(_WIN32)  
#error _WIN32 must be defined   // C1189  
#endif  
```  
  
 Můžete si také prohlédnout tuto chybu, pokud je sestavení projektu knihovny ATL s použitím **/ robust** MIDL – možnost kompilátoru. Použití **/ robust** přepínač tak, aby sestavení pouze [!INCLUDE[win2kfamily](../../c-runtime-library/includes/win2kfamily_md.md)] a novějších verzích systému Windows. Chcete-li tuto chybu, použijte jednu z následujících postupů:  
  
-   Změňte tento řádek v souboru dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
 na  
  
```  
#define _WIN32_WINNT 0x0500   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
-   Použití **Upřesnit** stránka vlastností v **MIDL** složky stránky vlastností k odebrání **/ robust** přepínače a potom zadejte **/no_robust** přepínač. Další informace najdete v tématu [MIDL – stránky vlastností: Upřesnit](../../ide/midl-property-pages-advanced.md).  
  
## <a name="see-also"></a>Viz také  
 [#define – direktiva (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)