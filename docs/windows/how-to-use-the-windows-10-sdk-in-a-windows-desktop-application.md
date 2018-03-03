---
title: "Postupy: použití Windows 10 SDK v aplikaci Windows Desktop | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f5e6f09b371c4d295b4bcdff469396a2671d22a
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Postupy: použití Windows 10 SDK v aplikaci Windows Desktop
Vytváříte-li ve Visual Studio 2017 klasické pracovní plochy projektu pro Windows, můžete ho je nastavený ve výchozím nastavení k vytvoření s verzí Windows 10 SDK, která byla nainstalována při zatížení C++ plocha byla nainstalována nebo poslední aktualizace. Tato verze sady Windows SDK je kompatibilní s všechny poslední verze systému Windows. Pokud chcete zacílit starší verze sady SDK, můžete otevřít projekt | Vlastnosti a volbou z jiné k dispozici v rozevírací nabídce verze sady SDK Windows SDK verze.  
  
 Od verze Visual Studio 2015 a Windows 10 SDK, byl knihovny CRT rozdělené na dvě části, jedna (ucrtbase) obsahuje funkce, které jsou přijatelné pro použití v univerzálních aplikací pro Windows a ten, který obsahuje všechno ostatní (vcruntime140). Vzhledem k tomu, že Windows 10 SDK obsahuje nové funkce, jako je například mnoho funkcí C99, musíte provést následující kroky, aby bylo možné používat tyto funkce. V tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).  
  
### <a name="to-target-the-windows-10-sdk"></a>Cíl Windows 10 SDK  
  
1.  Zkontrolujte, zda že je nainstalovaná sada Windows 10 SDK. Windows 10 SDK je nainstalován jako součást [nástrojů pro Windows 10](http://go.microsoft.com/fwlink/p/?linkid=617631).  
  
2.  Otevřete místní nabídku pro uzel projektu a zvolte **změnit cílový verze sady SDK**.  
  
     ![Změňte cíl verze sady SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     **Akce řešení zkontrolujte** otevře se dialogové okno.  
  
     ![Kontrola akcí řešení](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  V **Cílová platforma verze** rozevíracího seznamu vyberte verzi Windows 10 SDK, kterou chcete cílit. Klepněte na tlačítko OK na použití změny.  
  
     Všimněte si, že 8.1 v tomto kontextu odkazuje na verzi sady Windows SDK, která je zpětně kompatibilní s Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 a Windows Vista.  
  
     Pokud tento krok úspěšný, zobrazí se v okně výstupu následující text:  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  Otevřete vlastnosti projektu a v **konfigurační vlastnosti, Obecné** část, Všimněte si hodnot **Windows Cílová platforma verze**. Změna hodnoty zde má stejný účinek jako následujícího postupu. V tématu [Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md).  
  
     ![Cílová verze platformy](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     Tato akce změní hodnoty makra projektu, které zahrnují cesty hlavičkových souborů a soubory knihovny. Pokud chcete zobrazit, co se změnilo, v části Visual C++ adresáře v dialogovém okně Vlastnosti projektu zvolte jednu z vlastností, jako je například adresáře Include a potom vyberte otevřete rozevírací seznam a vyberte \<Upravit >. **Adresáře Include** otevře se dialogové okno.  
  
     ![Zahrnuje dialog pro adresáře](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     Vyberte **makra >>** tlačítko a přejděte dolů v seznamu makra a makra Windows SDK zobrazíte všechny nové hodnoty.  
  
     ![Windows SDK makra](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  Podle potřeby zopakujte pro další projekty a znovu sestavte řešení.  
  
### <a name="to-target-the-windows-81-sdk"></a>Cílovou sadu SDK Windows 8.1  
  
1.  Otevřete místní nabídku pro uzel projektu a zvolte **změnit cílový verze sady SDK**.  
  
2.  V rozevíracím seznamu Cílová verze platformy zvolte 8.1.  
  
## <a name="see-also"></a>Viz také  
 [Aplikace na ploše systému Windows (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)
