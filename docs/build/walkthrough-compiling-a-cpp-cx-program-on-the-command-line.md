---
title: "Návod: Kompilace C + +/ CX Program na příkazovém řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 677779aa8550869fe0859974b2aa4bbbb1c23d83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Návod: Kompilace C + +/ CX Program na příkazovém řádku
Můžete vytvořit programy Visual C++, které cílí na prostředí Windows Runtime a sestavit je na příkazovém řádku. Visual C++ podporuje rozšíření komponent v jazyce Visual C++ (C + +/ CX), který má operátory a další typy, jehož cílem je programovací model Windows Runtime. Můžete použít C + +/ CX pro vývoj aplikací pro Windows Phone 8.1, Windows Store a Windows desktop. Další informace najdete v tématu [A prohlídka c + +/ CX](http://msdn.microsoft.com/magazine/dn166929.aspx) a [rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md).  
  
 V tomto názorném postupu získáte pomocí textového editoru k vytvoření základní C + +/ CX programu a zkompilujte jej na příkazovém řádku. (Můžete použít vlastní C + +/ CX program místo zadání ten, který se zobrazí, nebo můžete použít C + +/ CX ukázka kódu z jiný článek nápovědy. Tato metoda je užitečná pro vytváření a testování malé modulů, které obsahují žádné elementy uživatelského rozhraní.)  
  
> [!NOTE]
>  Můžete také použít Visual Studio IDE zkompilovat C + +/ CX programy. Prostředí IDE zahrnuje návrh, ladění, emulace a podpora nasazení, která není k dispozici na příkazovém řádku, a proto doporučujeme vytvářet aplikace pro Windows Store pomocí rozhraní IDE. Další informace najdete v tématu [vytvoření základní aplikace pro C++ Store](http://msdn.microsoft.com/library/windows/apps/dn263168).  
  
## <a name="prerequisites"></a>Požadavky  
 Je potřeba pochopit základy jazyka C++.  
  
## <a name="compiling-a-ccx-program"></a>Kompilování C + +/ CX programu  
 Chcete-li povolit kompilace pro C + +/ CX, je nutné použít [/ZW](../build/reference/zw-windows-runtime-compilation.md) – možnost kompilátoru. Visual C++ compiler generuje soubor .exe, který cílí prostředí Windows Runtime a obsahuje odkazy na požadované knihovny.  
  
#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Kompilace C + +/ CX aplikace na příkazovém řádku  
  
1.  Otevřete **příkazový řádek vývojáře** okno. (Na **spustit** okně Otevřít **aplikace**. Otevřete **nástroje sady Visual Studio** složku s vaší verzí [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]a potom zvolte **příkazový řádek vývojáře** zástupce.) Další informace o tom, otevřete okno příkazového řádku vývojáře najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../build/building-on-the-command-line.md).  
  
     Přihlašovací údaje správce může být nutné úspěšně zkompilovat kód, v závislosti na operačním systému a konfigurace počítače. Spusťte okno příkazového řádku jako správce, otevřete místní nabídku pro **příkazový řádek vývojáře** a potom zvolte **spustit jako správce**.  
  
2.  Na příkazovém řádku zadejte **Poznámkový blok basiccx.cpp**.  
  
     Zvolte **Ano** po zobrazení výzvy k vytvoření souboru.  
  
3.  V poznámkovém bloku zadejte tyto řádky:  
  
    ```cpp  
    using namespace Platform;  
  
    int main(Platform::Array<Platform::String^>^ args)  
    {  
        Platform::Details::Console::WriteLine("This is a C++/CX program.");  
    }  
  
    ```  
  
4.  Na řádku nabídek zvolte **soubor**, **Uložit**.  
  
     Jste vytvořili Visual C++ zdrojový soubor, který používá prostředí Windows Runtime [obor názvů Platform](../cppcx/platform-namespace-c-cx.md) oboru názvů.  
  
5.  Na příkazovém řádku zadejte **/cl /EHsc /ZW basiccx.cpp Link /SUBSYSTEM:CONSOLE**. Cl.exe – kompilátor zkompiluje zdrojový kód do souboru .obj a poté spustí linkeru pro generování spustitelný program s názvem basiccx.exe. ( [/EHsc](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru Určuje model zpracování výjimek C++ a [/link](../build/reference/link-pass-options-to-linker.md) příznak určuje konzolové aplikace.)  
  
6.  Chcete-li basiccx.exe program, spusťte na příkazovém řádku, zadejte **basiccx**.  
  
     Program zobrazí tento text a bude ukončen:  
  
    ```Output  
    This is a C++/CX program.  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Sestavení C/C++ programů](../build/building-c-cpp-programs.md)   
 [Možnosti kompilátoru](../build/reference/compiler-options.md)