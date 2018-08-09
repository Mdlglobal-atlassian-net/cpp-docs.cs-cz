---
title: 'Návod: Vytvoření programu ve standardním C++ (C++) | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vcfirstapp
- vccreatefirst
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4f3f01ab95237a0401394d429443804ce65a4385
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017325"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Návod: Vytvoření programu ve standardním C++ (C++)
Visual C++ v sadě Visual Studio integrované vývojové prostředí (IDE) slouží k vytvoření standardního programu C++. Podle kroků v tomto podrobném návodu, můžete vytvořit projekt, přidejte do projektu nový soubor, upravte soubor tak přidáním kódu jazyka C++ a potom zkompilujete a spustíte program pomocí [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 Můžete zadat vlastní program C++, nebo použijte jednu z ukázkových programů. Ukázkový program v tomto návodu je konzolová aplikace. Tato aplikace používá `set` kontejneru ve standardní knihovně jazyka C++.  
  
 Visual C++ v souladu se standardem 2003 C++, s následujícími hlavními výjimkami: vyhledávání dvoufázová názvu, specifikace výjimek a export. Kromě toho Visual C++ podporuje několik funkcí C ++ 0 x, například výrazy lambda, auto, static_assert, odkazy rvalue a externí šablony.  
  
> [!NOTE]
>  Pokud dodržování standardu je potřeba použít `/Za` – možnost kompilátoru zakázat rozšíření Microsoft pro standardní. Další informace najdete v tématu [/Za, /Ze (zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Předpokladem práce s tímto návodem je znalost základů jazyka C++.  
  
### <a name="to-create-a-project-and-add-a-source-file"></a>Vytvoření projektu a přidání zdrojového souboru  
  
1.  Vytvořte projekt tak, že označíte **nový** na **souboru** nabídky a pak levým na **projektu**.  
  
2.  V **Visual C++** podokně typů projektů, klikněte na tlačítko **Windows Desktop**a potom klikněte na tlačítko **Konzolová aplikace Windows**.  
  
3.  Zadejte název projektu.  
  
     Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění pro projekt.  
  
     Klikněte na tlačítko **OK** pro vytvoření projektu.  
  
4.  Pokud **Průzkumníka řešení** se nezobrazuje na **zobrazení** nabídky, klikněte na tlačítko **Průzkumníka řešení**.  
  
5.  Přidání nového zdrojového souboru do projektu, následujícím způsobem.  
  
    1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **zdrojové soubory** složku, přejděte na příkaz **přidat**a potom klikněte na tlačítko **nová položka**.  
  
    2.  V **kód** uzel, klikněte na tlačítko **soubor C++ (.cpp)**, zadejte název souboru a pak klikněte na tlačítko **přidat**.  
  
     Soubor .cpp se zobrazí v **zdrojové soubory** složky **Průzkumníka řešení**, a soubor je otevřen v editoru sady Visual Studio.  
  
6.  V souboru v editoru zadejte platný program C++ používající standardní knihovny C++, nebo zkopírujte jeden z ukázkových programů a vložte ho do souboru.  
  
7.  Uložte soubor.  
  
8. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     **Výstup** okně zobrazí informace o průběhu kompilace, například umístění protokolu sestavení a napište zprávu, která označuje stav sestavení.  
  
9. Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.  
  
     Pokud jste použili ukázkový program, zobrazí se okno příkazového řádku a ukazuje, zda jsou určitá celá čísla nalezena v množině.  
  
## <a name="next-steps"></a>Další kroky  
 **Předchozí:** [konzolové aplikace v jazyce Visual C++](../windows/console-applications-in-visual-cpp.md). **Další krok:**[návod: kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)