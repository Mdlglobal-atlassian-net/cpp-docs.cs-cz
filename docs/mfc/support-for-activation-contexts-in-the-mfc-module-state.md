---
title: "Podpora kontextů aktivace ve stavu modulu MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a9a15941848a9e8d5bdf35dfebf273f7684fbb8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Podpora kontextů aktivace ve stavu modulu MFC
MFC vytvoří aktivační kontext pomocí prostředku manifestu poskytované modulem uživatele. Další informace o vytváření kontexty aktivace najdete v následujících tématech:  
  
-   [Kontexty aktivace](http://msdn.microsoft.com/library/aa374153)  
  
-   [Manifesty aplikací](http://msdn.microsoft.com/library/aa374191)  
  
-   [Manifesty sestavení](http://msdn.microsoft.com/library/aa374219)  
  
## <a name="remarks"></a>Poznámky  
 Při čtení těchto témat Windows SDK, Všimněte si, že mechanismus MFC aktivační kontext podobá aktivační kontext sady Windows SDK, s tím rozdílem, že MFC nepoužívá rozhraní API systému Windows SDK aktivační kontext.  
  
 Kontext aktivace funguje v aplikacích MFC, knihovny DLL uživatele a MFC – knihovny DLL rozšíření následujícími způsoby:  
  
-   Aplikace MFC použít prostředek ID 1 pro jejich prostředku manifestu. V takovém případě knihovny MFC nevytváří vlastní aktivační kontext, ale používá výchozí kontext aplikace.  
  
-   Uživatel MFC – knihovny DLL pomocí prostředku ID 2 pro jejich prostředku manifestu. MFC tady, vytvoří pro každou knihovnu DLL uživatele aktivační kontext, takže jiný uživatel knihovny DLL můžete použít různé verze stejné knihovny (například knihovna běžné ovládací prvky).  
  
-   MFC – knihovny DLL rozšíření spoléhají na jejich hostování aplikace nebo uživatele knihovny DLL k vytvoření jejich aktivační kontext.  
  
 I když kontextu stav aktivace se dají změnit pomocí postupů popsaných v části [pomocí rozhraní API aktivační kontext](http://msdn.microsoft.com/library/aa376620), pomocí mechanismu MFC aktivační kontext může být užitečné při vývoji založené na knihovnu DLL modulu plug-in architektury Pokud to není snadno (nebo není možné) ručně přepnout stavu aktivace před a po jednotlivých volání externí moduly plug-in.  
  
 Aktivační kontext je vytvořen v [afxwininit –](../mfc/reference/application-information-and-management.md#afxwininit). Byla v `AFX_MODULE_STATE` destruktor. Popisovač aktivační kontext je uložen v `AFX_MODULE_STATE`. (`AFX_MODULE_STATE` je popsaná v [afxgetstaticmodulestate –](reference/extension-dll-macros.md#afxgetstaticmodulestate).)  
  
 [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) makro aktivuje a deaktivuje aktivační kontext. `AFX_MANAGE_STATE`je povolený pro statické knihovny MFC a také MFC – knihovny DLL, a umožňuje MFC kód na provedení v správný aktivační kontext Vybraná knihovna DLL uživatele.  
  
## <a name="see-also"></a>Viz také  
 [Kontexty aktivace](http://msdn.microsoft.com/library/aa374153)   
 [Manifesty aplikací](http://msdn.microsoft.com/library/aa374191)   
 [Manifesty sestavení](http://msdn.microsoft.com/library/aa374219)   
 [Afxwininit –](../mfc/reference/application-information-and-management.md#afxwininit)   
 [Afxgetstaticmodulestate –](reference/extension-dll-macros.md#afxgetstaticmodulestate)   
 [AFX_MANAGE_STATE –](reference/extension-dll-macros.md#afx_manage_state)

