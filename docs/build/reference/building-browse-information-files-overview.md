---
title: "Soubory informace o vytváření procházení: Přehled | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f5b369d5a708e0ee56df635234c68ee88a31af48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="building-browse-information-files-overview"></a>Sestavení souborů informací o procházení: Přehled
K vytvoření informací procházení pro procházení symbol, kompilátor vytvoří soubor .sbr pro každý zdrojový soubor ve vašem projektu, pak BSCMAKE. EXE řetězí soubory .sbr do jednoho souboru BSC programem.  
  
 Generování souborů .sbr a .bsc trvá určitou dobu, takže Visual C++ vypne tyto funkce ve výchozím nastavení. Pokud chcete procházet aktuální informace, musíte zapnout možnosti procházení a znovu sestavte projekt.  
  
 Použití [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) nebo [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md) říct kompilátor vytvoří soubory .sbr. Pokud chcete vytvořit soubory .bsc, můžete volat [BSCMAKE](../../build/reference/bscmake-command-line.md) z příkazového řádku. Pomocí nástroje BSCMAKE z příkazového řádku získáte přesnější kontrolu nad manipulaci soubory s informacemi o procházení. V tématu [BscMake – odkaz](../../build/reference/bscmake-reference.md) Další informace.  
  
> [!TIP]
>  Můžete zapnout generování souboru .sbr, ale ponechte generování souboru .bsc vypnutý. To poskytuje fast sestavení, ale taky umožňuje rychle vytvořit soubor nový .bsc tím, že na generování souboru .bsc a sestavení projektu.  
  
 Můžete snížit čas, paměť a místo na disku požadované k sestavení souboru BSC snížením velikosti souboru BSC programem.  
  
 V tématu [Obecná stránka vlastností (projekt)](../../ide/general-property-page-project.md) informace o tom, jak vytvořit soubor prohlížeče ve vývojovém prostředí.  
  
### <a name="to-create-a-smaller-bsc-file"></a>Chcete-li vytvořit menší soubor .bsc  
  
1.  Použití [možnosti příkazového řádku BSCMAKE](../../build/reference/bscmake-options.md) vyloučit informace z soubor s informacemi o procházení.  
  
2.  Vynechte lokální symboly v jeden nebo více souborů .sbr při kompilování nebo sestavení.  
  
3.  Pokud soubor objektu neobsahuje informace potřebné pro vaše aktuální fázi ladění, vynechejte jeho souboru .sbr z příkazu BSCMAKE po novém sestavení soubor s informacemi o procházení.  
  
### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Kombinování procházet informace z několika projektů do prohlížeče jednoho souboru (.bsc)  
  
1.  Buď nemáte vytvoření .bsc souboru na úrovni projektu nebo použijte přepínač/n zabránit ke zkrácení soubory .sbr.  
  
2.  Jakmile jsou všechny projekty vytvořen, spusťte BSCMAKE s všechny soubory .sbr jako vstup. Zástupné znaky. Například pokud jste měli adresáře projektu C:\X, C:\Y a C:\Z se soubory .sbr v nich a jste chtěli kombinovat všechny do jednoho souboru BSC programem, použijte BSCMAKE C:\X\\*.sbr C:\Y\\\*.sbr C:\Z\\\*. /o c:\whatever_directory\combined.bsc SBR k vytvoření souboru kombinované BSC programem.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)   
 [BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)