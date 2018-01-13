---
title: Druhy knihoven DLL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47ce4a9264a59f88f22cd40bc3b6d6620c9702c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="kinds-of-dlls"></a>Druhy knihoven DLL
Toto téma obsahuje informace, které vám pomohou určit druh knihovny DLL pro sestavení.  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>Různé druhy knihoven DLL, které jsou k dispozici  
 Pomocí Visual C++, můžete vytvořit Win32 knihovny DLL v jazyka C nebo C++, která nepoužívají knihovna Microsoft Foundation Class (MFC). Můžete vytvořit projekt knihovny MFC DLL pomocí Průvodce aplikací Win32.  
  
 Samotné knihovny MFC je k dispozici, buď statických knihoven nebo v počtu knihovny DLL pomocí Průvodce MFC DLL. Pokud vaše knihovna DLL je použití prostředí MFC, Visual C++ podporuje tři různé scénáře vývoje knihovny DLL:  
  
-   Sestavování běžný MFC DLL, která staticky propojuje MFC  
  
-   Sestavování běžný MFC DLL, která dynamicky propojuje MFC  
  
-   Sestavování knihovnu DLL, která vždy dynamicky propojené knihovny MFC  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Knihovny DLL mimo MFC – přehled](../build/non-mfc-dlls-overview.md)  
  
-   [Regulární knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Regulární knihovny MFC DLL dynamicky propojené s MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Rozšiřující knihovny MFC DLL: Přehled](../build/extension-dlls-overview.md)  
  
-   [Jaký druh knihovny DLL používat](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a>Rozhodování, jaký druh knihovny DLL pro použití  
 Pokud vaše knihovna DLL nepoužívá MFC, použijte k vytvoření non - MFC Win32 DLL Visual C++. Propojování vaší knihovny DLL do MFC (staticky nebo dynamicky) zabere podstatné místo na disku a paměť. Pokud vaše knihovna DLL aktuálně používá MFC, by neměl MFC propojit.  
  
 Pokud vaše knihovna DLL použijete MFC a použije MFC nebo mimo MFC aplikací, musíte sestavit běžné knihovny DLL MFC, který dynamicky odkazuje na knihovny MFC nebo běžné knihovny DLL MFC, který staticky odkazuje na knihovny MFC. Ve většině případů budete chtít pravděpodobně používat běžné knihovny DLL MFC, který dynamicky odkazuje na knihovny MFC, protože budou mnohem menší velikost souboru knihovny DLL a úspory v paměti pomocí sdílené verze knihovny MFC může být důležité. Pokud se staticky propojíte s knihovnou MFC, velikost souboru vaší knihovny DLL bude větší a potenciálně trvat až paměť navíc, protože je načten jeho vlastní privátní kopii kódu knihovny MFC.  
  
 Vytváření knihovny DLL, která propojuje ke knihovně MFC je rychlejší než vytváření knihovny DLL, který staticky odkazuje na knihovny MFC, protože není potřeba propojit MFC sám sebe. To platí hlavně v linkeru musí kde compact informace o ladění sestavení pro ladění. Pomocí propojení s knihovny DLL, která již obsahuje informace o ladění, je menší informace o ladění, chcete-li komprimovat v rámci vaší knihovny DLL.  
  
 Jednou z nevýhod k dynamickému propojení s knihovnou MFC je s knihovny DLL musí distribuovat sdílené knihovny DLL Mfcx0.dll a Msvcrxx.dll (nebo podobné soubory). Knihovny MFC DLL jsou volně redistributable, ale stále je nutné nainstalovat knihovny DLL v instalačním programu. Kromě toho můžete musíte poskytnout Msvcrxx.dll, který obsahuje běhové knihovny jazyka C, který se používá jak podle vašeho programu a knihovny MFC DLL sami.  
  
 Pokud vaše knihovna DLL se používá pouze spustitelné soubory knihovny MFC, máte možnost volby mezi vytváření běžné knihovny MFC DLL nebo knihovnu DLL. Pokud vaše knihovna DLL implementuje použitelné třídy odvozené z existujících tříd MFC nebo potřebujete předat objekt odvozené MFC mezi aplikací a knihovny DLL, musíte sestavit knihovnu DLL.  
  
 Pokud vaše knihovna DLL dynamicky odkazuje na knihovny MFC a knihovny MFC DLL může být znovu distribuovány s knihovny DLL. Tato architektura je zvláště užitečná pro sdílení knihovny tříd mezi více spustitelné soubory ušetřit místo na disku a minimalizovat využití paměti.  
  
 Starší než verze 4.0, Visual C++ pouze podporované dva druhy knihoven DLL, které používají MFC: knihovny USRDLL a AFXDLL. Regulární knihovny MFC DLL staticky propojené do MFC mají stejné vlastnosti jako dosavadní USRDLL. MFC – knihovny DLL rozšíření mají stejné vlastnosti jako dřívější AFXDLL.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Knihovny DLL mimo MFC – přehled](../build/non-mfc-dlls-overview.md)  
  
-   [Regulární knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Regulární knihovny MFC DLL dynamicky propojené s MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Rozšiřující knihovny MFC DLL: Přehled](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)