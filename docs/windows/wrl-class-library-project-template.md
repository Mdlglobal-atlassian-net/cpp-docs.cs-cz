---
title: "Šablona projektu knihovny tříd WRL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 628b0852-89e5-44f8-bf58-a09762bda15c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13fc476f696bdd2cb17ed58c496c63747db90322
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="wrl-class-library-project-template"></a>Šablona projektu knihovny tříd WRL
Pokud používáte Visual Studio k zápisu projektu Windows Runtime C++ šablony knihovny (WRL), může výrazně zjednodušit úlohu stažením šablona projektu knihovny tříd WRL.  
  
> [!NOTE]
>  Pokud budete muset ručně aktualizovat nastavení projektu pro existujícího projektu, přečtěte si téma [knihovny DLL (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh699881\(v=vs.110\).aspx).  
  
## <a name="download-the-wrl-project-template"></a>Stáhnout šablona projektu knihovny WRL  
 Visual Studio neposkytuje šablonu pro projekty knihovna šablon C++ prostředí Windows Runtime. Chcete-li stáhnout šablona projektu, který vytvoří knihovnu základní třída pro univerzální platformu Windows aplikace s knihovna šablon C++ prostředí Windows Runtime.  
  
#### <a name="to-download-the-wrl-project-template"></a>Chcete-li stáhnout šablona projektu knihovny WRL  
  
1.  Na řádku nabídek zvolte **soubor**, **nový projekt**.  
  
2.  V levém podokně **nový projekt** dialogové okno, vyberte **Online**a potom vyberte **šablony**.  
  
3.  V **Hledat online šablony** pole v pravém horním rohu, typ `WRL Class Library`. Pokud šablona se zobrazí ve výsledcích hledání, vyberte **OK** tlačítko.  
  
4.  V **stáhněte a nainstalujte** dialogové okno, pokud souhlasíte s licencování podmínek, vyberte **nainstalovat** tlačítko.  
  
5.  Po instalaci šablony vytvořte projekt tak, že zvolíte **soubor**, **nový projekt**a potom vyberete `WRLClassLibrary` šablony. Projektu vytvoří knihovnu DLL.  
  
## <a name="examples-that-use-the-project-template"></a>Příklady, které používají v šabloně projektů  
 Čtení [návod: vytvoření základní komponenty prostředí Windows Runtime](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md) pro příklad, který používá tato šablona k vytvoření komponent prostředí Windows Runtime.  
  
## <a name="what-the-project-template-provides"></a>Poskytuje šablony projektu  
 Šablona projektu poskytuje:  
  
-   .idl soubor, který deklaruje MIDL atributy pro základní rozhraní jeho implementaci třídy. Tady je příklad.  
  
     [!code-cpp[wrl-project-template#1](../windows/codesnippet/CPP/wrl-class-library-project-template_1.idl)]  
  
-   Sada soubor, který definuje implementaci třídy. Tady je příklad.  
  
     [!code-cpp[wrl-project-template#2](../windows/codesnippet/CPP/wrl-class-library-project-template_2.cpp)]  
  
     [RuntimeClass](../windows/runtimeclass-class.md) základní třídou pomáhá spravovat odkaz na globální všech objektů v modulu a deklaruje metody [IUnknown](http://msdn.microsoft.com/en-us/33f1d79a-33fc-4ce5-a372-e08bda378332) a [IInspectable](http://msdn.microsoft.com/en-us/0657e51f-d4c0-46c6-927d-b01e54b6846c) rozhraní. [Inspectableclass –](../windows/inspectableclass-macro.md) implementuje makro `IUnknown` a `IInspectable`. [Activatableclass –](../windows/activatableclass-macros.md) makro vytvoří objekt factory třídy, který vytváří instance třídy.  
  
-   soubor s názvem module.cpp, která definuje knihovny exportuje `DllMain`, `DllCanUnloadNow`, `DllGetActivationFactory`, a `DllGetClassObject`.  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)