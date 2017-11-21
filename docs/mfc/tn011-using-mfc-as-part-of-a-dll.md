---
title: "TN011: Použití prostředí MFC jako součásti knihovny DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.dll
dev_langs: C++
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 312451f40b19375dcef9d4a68b2d1bf3f3ae2562
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: Použití prostředí MFC jako součásti knihovny DLL
Tato poznámka popisuje regulární knihovny MFC DLL, který vám umožní používat knihovny MFC jako součást Windows dynamická knihovna (DLL). Přitom se předpokládá, že jste obeznámeni s knihovny DLL systému Windows a jak sestavit je. Informace o MFC – rozšiřující knihovny DLL, pomocí kterého můžete vytvořit rozšíření ke knihovně MFC najdete v části [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md).  
  
## <a name="dll-interfaces"></a>Knihovny DLL rozhraní  
 regulární knihovny MFC DLL předpokládají, rozhraní mezi aplikací a knihovny DLL jsou určené v C jako funkce nebo explicitně exportovaný třídy. Třída rozhraní MFC nelze exportovat.  
  
 Pokud chcete použít MFC knihovny DLL i aplikace, mají obě volba použít sdílené verze knihovny MFC nebo staticky propojit kopie knihovny. Aplikace a soubor DLL může obojí použijte jeden z standardní verze knihovny MFC.  
  
 regulární knihovny MFC DLL mají několik výhod:  
  
-   Aplikace, která používá knihovnu DLL není nutné používat MFC a nemá být aplikace Visual C++.  
  
-   S regulární knihovny MFC DLL, která buď staticky velikost knihovnu DLL závisí pouze na rutiny modulu runtime MFC a C, které se používají a propojená.  
  
-   Regulární knihovny MFC DLL, která dynamicky propojené s knihovnou MFC může být úspory v paměti pomocí sdílené verze knihovny MFC významné. Nicméně je nutné distribuovat sdílené knihovny DLL Mfc*\<verze >*.dll a Msvvcrt*\<verze >*.dll s knihovnou DLL.  
  
-   Knihovna DLL je nezávisle na tom, jak jsou implementované třídy. Návrhu DLL exportuje pouze do rozhraní API, které chcete. Výsledkem je pokud se změní implementace, regulární MFC – knihovny DLL musí být stále platné.  
  
-   S regulární knihovny MFC DLL, která staticky propojit MFC pokud DLL a aplikace použít MFC, neexistují žádné problémy s aplikací, který chce jinou verzi knihovny MFC DLL nebo naopak. Protože knihovny MFC je staticky propojené do každé knihovny DLL nebo EXE, neexistuje žádná otázka, o kterou verzi máte.  
  
## <a name="api-limitations"></a>Omezení rozhraní API  
 Některé funkce MFC se nevztahuje na knihovnu DLL verze, buď z důvodu technická omezení nebo proto, že tyto služby jsou obvykle poskytuje aplikace. V aktuální verzi knihovny MFC je jenom funkce, která se nedá použít `CWinApp::SetDialogBkColor`.  
  
## <a name="building-your-dll"></a>Vytváření knihovny DLL  
 Při kompilování regulární knihovny DLL MFC, který staticky propojit MFC symboly `_USRDLL` a `_WINDLL` musí být definován. Váš kód knihovny DLL musí být zkompilovány také s následující přepínače kompilátoru:  
  
- **/ D_WINDLL** označuje, že je kompilace pro knihovny DLL  
  
- **/ D_USRDLL** určuje vytváříte běžné knihovny MFC DLL  
  
 Musíte také definovat tyto symboly a použít tyto přepínače kompilátoru při kompilaci regulární knihovny MFC DLL, která dynamicky propojené s knihovnou MFC. Kromě toho symbol `_AFXDLL` musí být definovaný a váš kód knihovny DLL musí být zkompilovány s:  
  
- **/ D_AFXDLL** Určuje, že vytváříte běžné knihovny DLL MFC, který dynamicky odkazuje na knihovny MFC  
  
 Rozhraní (API), mezi aplikací a knihovny DLL musí být explicitně exportován. Doporučujeme, abyste definovat vašich rozhraní jako malou šířkou pásma a používat pouze C rozhraní, pokud je to možné. Přímé C rozhraní se snadněji udržují než složitější třídy jazyka C++.  
  
 Místní vaše rozhraní API v samostatných hlavičku, která může být zahrnuta v souborech C a C++. Najdete v hlavičce ScreenCap.h v ukázce MFC rozšířené koncepty [DLLScreenCap](../visual-cpp-samples.md) příklad. Export funkcí, zadejte je do `EXPORTS` části souboru definice modulu (. DEF) nebo `__declspec(dllexport)` na vaše definice funkcí. Použití `__declspec(dllimport)` naimportujte tyto funkce spustitelný soubor klienta.  
  
 Je nutné přidat `AFX_MANAGE_STATE` makro na začátku všech exportovaných funkcí v běžných knihovnách DLL MFC, která dynamicky propojené s knihovnou MFC. Toto makro nastaví aktuální stav modulu pro knihovnu DLL. Použití tohoto makra, přidejte následující řádek kódu na začátek funkce exportované z knihovny DLL:  
  
 `AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`  
  
## <a name="winmain---dllmain"></a>WinMain – -> DllMain  
 Knihovny MFC definuje standardní Win32 `DllMain` vstupního bodu, který inicializuje vaše [CWinApp](../mfc/reference/cwinapp-class.md) odvozené objektu jako v typické aplikaci MFC. Umístěte všechny inicializace specifické knihovny DLL v [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) metoda jako v typické aplikaci MFC.  
  
 Všimněte si, že [CWinApp::Run](../mfc/reference/cwinapp-class.md#run) mechanismus se nevztahuje na knihovnu DLL, protože aplikace vlastní hlavní message pump. Pokud vaše knihovna DLL zobrazí nemodální dialogová okna nebo má své vlastní okno hlavního rámce, hlavní "message pump" vaší aplikace musí volat rutinu Export knihovny DLL, která volá [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).  
  
 Viz ukázka DLLScreenCap pro použití této funkce.  
  
 `DllMain` Funkce, která poskytuje MFC zavolá [CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) metoda vaší třídy, který je odvozený od `CWinApp` před uvolněním knihovnu DLL.  
  
## <a name="linking-your-dll"></a>Propojování vaší knihovny DLL  
 S regulární knihovny MFC DLL, která buď staticky je nutné propojit knihovny DLL s Nafxcwd.lib nebo Nafxcw.lib a s verzí runtimes C s názvem Libcmt.lib. Tyto knihovny jsou předem vytvořené a může být nainstalován zadáním je při spuštění instalačního programu Visual C++.  
  
## <a name="sample-code"></a>Ukázkový kód  
 Naleznete v ukázce MFC rozšířené koncepty programu DLLScreenCap kompletní příklad. Následuje několik zajímavé skutečností, které je Poznámka: v této ukázce:  
  
-   Příznaky kompilátoru knihovny DLL a aplikace, se liší.  
  
-   Odkaz čar a. DEF soubory pro knihovnu DLL a aplikace se liší.  
  
-   Aplikace, která používá knihovnu DLL nemusí být v jazyce C++.  
  
-   Rozhraní mezi aplikací a knihovny DLL je rozhraní API, který je použitelný pro C nebo C++ a exportu s DLLScreenCap.def.  
  
 Následující příklad ilustruje rozhraní API, která je definována v knihovně MFC DLL, který staticky odkazuje na MFC běžný. V tomto příkladu je součástí deklaraci `extern "C" { }` bloku pro C++ uživatele. To má několik výhod. První má vaše rozhraní API knihovny DLL použitelné mimo jazyk C++ klientskými aplikacemi. Druhý snižuje režijní náklady na knihovnu DLL, protože úprava názvu C++ se nepoužije pro exportovaný název. Nakonec umožňuje jednodušší chcete explicitně přidat. DEF souboru (pro export podle pořadových) bez nutnosti starat o úprava názvu.  
  
```  
#ifdef __cplusplus  
extern "C" {  
#endif  /* __cplusplus */  
 
struct TracerData  
{  
    BOOL bEnabled;  
    UINT flags;  
};  
 
BOOL PromptTraceFlags(TracerData FAR* lpData);

 
#ifdef __cplusplus  
}  
#endif  
```  
  
 Struktury využívané prostředím rozhraní API není odvozen od třídy knihovny MFC a jsou definovány v hlavičce rozhraní API. Tím se sníží složitost rozhraní mezi knihovnou DLL a aplikace a umožňuje použít knihovnu DLL programy C.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

