---
title: 'Postupy: použití Windows 10 SDK v desktopové aplikace Windows | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07cd0d02edc586697e42e4733df478a7ae394e0f
ms.sourcegitcommit: 9ad287c88bdccee2747832659fe50c2e5d682a0b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39034777"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Postupy: použití Windows 10 SDK v desktopové aplikaci Windows
Při vytváření klasický desktopový projekt Windows v sadě Visual Studio 2017 je nastaven ve výchozím nastavení k sestavení s verzí Windows 10 SDK, která byla nainstalována při C++ Desktop workload byla nainstalována nebo naposledy aktualizována. Tato verze sady Windows SDK je kompatibilní s Windows 7 a novější. Zobrazit [pomocí hlavičky Windows](/windows/desktop/WinProg/using-the-windows-headers) Další informace o cílení na konkrétní verze Windows.

Pokud chcete cílit na starší verzi sady SDK, můžete otevřít **projektu | Vlastnosti** a vyberte si z dostupných v rozevíracím seznamu verzi sady SDK Windows SDK verze.
  
 Od verze Visual Studio 2015 a sada Windows 10 SDK, knihovny CRT se rozdělené na dvě části, jeden (ucrtbase), který obsahuje funkce, které jsou přijatelné pro univerzální aplikace pro Windows a ta, která obsahuje všechno ostatní (vcruntime140). Od Windows 10 SDK obsahuje nové funkce, jako je například mnoho funkcí C99, budete muset postupujte podle těchto kroků, aby bylo možné použít dané funkce. Zobrazit [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).  
  
### <a name="to-target-the-windows-10-sdk"></a>Na cíl Windows 10 SDK  
  
1.  Ujistěte se, že je nainstalovaná sada Windows 10 SDK. Windows 10 SDK je nainstalována jako součást **vývoj desktopových aplikací pomocí C++** pracovního vytížení. Je k dispozici na samostatnou verzi [soubory ke stažení a nástroje pro Windows 10](https://developer.microsoft.com/windows/downloads).

  
2.  Otevřete místní nabídku pro uzel projektu a zvolte **změnit cílení verze sady SDK**.  
  
     ![Výsledkem změny cílení verze SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     **Akce řešení zkontrolujte** se zobrazí dialogové okno.  
  
     ![Zkontrolovat akce řešení](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  V **verze cílové platformy** rozevíracího seznamu vyberte verzi Windows 10 SDK, kterou chcete cílit. Klikněte na tlačítko OK na použití změny.  
  
     Všimněte si, že v tomto kontextu 8.1 odkazuje na verzi sady Windows SDK, která je zpětně kompatibilní s Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 a Windows Vista.  
  
     Pokud tento krok je úspěšná, v okně výstupu se zobrazí následující text:  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  Otevřete vlastnosti projektu a **vlastnosti konfigurace, Obecné** části, Všimněte si, že hodnoty **verze cílové platformy Windows**. Změna hodnoty tady má stejný účinek jako tohoto postupu. Zobrazit [Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md).  
  
     ![Cílit na verzi platformy](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     Tato akce změní hodnoty projektová makra, které zahrnují cesty k souborů hlaviček a soubory knihovny. Chcete-li zjistit, co změnil v sekci adresáře Visual C++ v dialogovém okně vlastností projektu zvolte jednu z vlastností, jako je například adresáře Include, zvolte otevřete rozevírací seznam a zvolte \<Upravit >. **Adresáře souborů k zahrnutí** se zobrazí dialogové okno.  
  
     ![Zahrnout adresáře dialogovému oknu](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     Zvolte **makra >>** tlačítko a přejděte dolů na seznamu makra a makra sady Windows SDK zobrazíte všechny nové hodnoty.  
  
     ![Windows SDK makra](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  Opakujte pro další projekty podle potřeby a znovu sestavte řešení.  
  
### <a name="to-target-the-windows-81-sdk"></a>Cílení Windows 8.1 SDK  
  
1.  Otevřete místní nabídku pro uzel projektu a zvolte **změnit cílení verze sady SDK**.  
  
2.  V rozevíracím seznamu verzi cílové platformy zvolte 8.1.  
  
## <a name="see-also"></a>Viz také  
 [Desktopové aplikace Windows (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)
