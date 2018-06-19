---
title: Export tříd řetězec pomocí CStringT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7510b1f44f49d17211c71419f4dde5a6e6a78974
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356393"
---
# <a name="exporting-string-classes-using-cstringt"></a>Export tříd řetězec pomocí CStringT
V minulosti jste vývojáři MFC odvozené z `CString` se specializují vlastní řetězec třídy. V sadě Microsoft Visual C++ .NET (MFC 8.0) [CString](../atl-mfc-shared/using-cstring.md) třída byla nahrazena šablony třídy s názvem [CStringT](../atl-mfc-shared/reference/cstringt-class.md). To poskytuje několik výhod:  
  
-   Je povolena MFC `CString` třídy mají být použity v ATL projekty bez propojení větší statické knihovny MFC nebo DLL.  
  
-   S novým `CStringT` třída šablony, můžete přizpůsobit `CString` chování pomocí parametrů šablony, které určují vlastnosti znak, podobně jako šablon ve standardní knihovně C++.  
  
-   Při exportu třídě řetězec z knihovny DLL pomocí `CStringT`, kompilátor také automaticky vyexportuje `CString` základní třídy. Vzhledem k tomu `CString` je sám třídu šablony může být vytvořeno kompilátorem, pokud se použije, pokud kompilátor si je vědoma, `CString` je naimportované z knihovny DLL. Pokud jste migrovali projekty Visual C++ 6.0 na Visual C++ .NET, může viděli jste symbol chybami linkeru pro násobení definované `CString` z důvodu kolizí z `CString` naimportované z knihovny DLL a místně instancí verze. Správný způsob, jak k tomu je popsaný níže. Další informace o tomto problému najdete v článku znalostní báze Knowledge Base "propojování chyby při importu CString odvozené třídy" (Q309801) v [ http://support.microsoft.com/default.aspx ](http://support.microsoft.com/default.aspx).  
  
 V následujícím scénáři způsobí, že linkeru k vytvoření chyby symbol pro násobkem definovaných tříd. Předpokládejme, že exportujete `CString`-odvozené třídy (`CMyString`) z knihovnu DLL:  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]  
  
 Příjemce kód používá kombinaci `CString` a `CMyString`. "MyString.h" není součástí předkompilovaných hlaviček a některé využití `CString` nemá `CMyString` viditelné.  
  
 Předpokládejme, že používáte `CString` a `CMyString` třídy v samostatných zdrojové soubory, Source1.cpp a Source2.cpp. V Source1.cpp, použijete `CMyString` a #include MyString.h. V Source2.cpp, použijete `CString`, ale nechcete #include MyString.h. V takovém případě bude stěžují linkeru `CStringT` násobkem definovaný. Je to způsobeno `CString` se obě naimportované z knihovny DLL, který exportuje `CMyString`a mohl vytvořit jeho instanci místně kompilátoru prostřednictvím `CStringT` šablony.  
  
 Chcete-li vyřešit tento problém, postupujte takto:  
  
 Export `CStringA` a `CStringW` (a potřebné základní třídy) z MFC90. KNIHOVNY DLL. Projekty, které zahrnují MFC vždy použije MFC DLL exportovat `CStringA` a `CStringW`, jako v předchozích implementacích MFC.  
  
 Pak vytvořte exportovatelný odvozené třídy pomocí `CStringT` šablony, jako `CStringT_Exported` je níže, například:  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]  
  
 V AfxStr.h, nahradí předchozí `CString`, `CStringA`, a `CStringW` – definice TypeDef následujícím způsobem:  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]  
  
 Existuje několik aspektů:  
  
-   Neexportujte `CStringT` samotné vzhledem k tomu, že to způsobí, že pouze ATL projekty pro export specializované `CStringT` třídy.  
  
-   Pomocí exportovatelný odvozené třídy z `CStringT` minimalizuje museli znovu implementovat `CStringT` funkce. Další kód je omezený na předávání pro konstruktory `CStringT` základní třídy.  
  
-   `CString`, `CStringA`, a `CStringW` pouze by měl být označen `__declspec(dllexport/dllimport)` když vytváříte pomocí knihovny MFC sdílené knihovny DLL. Pokud propojení s statickou knihovnou MFC, by neměl označit tyto třídy exportovat; v opačném případě interní použití `CString`, `CStringA`, a `CStringW` uvnitř uživatele knihovny DLL označíte `CString` také exportovat.  
  
## <a name="related-topics"></a>Související témata  
 [CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)  
  
## <a name="see-also"></a>Viz také  
 [Pomocí CStringT](../atl-mfc-shared/using-cstringt.md)   
 [CString – použití](../atl-mfc-shared/using-cstring.md)

