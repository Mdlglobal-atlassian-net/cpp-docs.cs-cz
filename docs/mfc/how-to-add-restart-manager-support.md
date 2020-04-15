---
title: 'Postupy: Přidání podpory správce restartování'
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 7cf3fede663a7c4bc85573e17dd9c2f8bf3622b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373320"
---
# <a name="how-to-add-restart-manager-support"></a>Postupy: Přidání podpory správce restartování

Správce restartování je funkce přidaná do sady Visual Studio pro operační systémy Windows Vista nebo novější. Správce restartování přidá podporu pro vaši aplikaci, pokud se neočekávaně zavře nebo restartuje. Chování správce restartování závisí na typu aplikace. Pokud je vaše aplikace editor dokumentů, správce restartování povolil aplikaci automaticky uložit stav a obsah všech otevřených dokumentů a restartuje aplikaci po neočekávaném uzavření. Pokud vaše aplikace není editor dokumentů, správce restartování restartuje aplikaci, ale nemůže uložit stav aplikace ve výchozím nastavení.

Po restartování aplikace zobrazí dialogové okno úlohy, pokud je aplikace Unicode. Pokud se jedná o aplikaci ANSI, aplikace zobrazí okno se zprávou systému Windows. V tomto okamžiku se uživatel rozhodne, zda obnoví automaticky uložené dokumenty. Pokud uživatel automaticky uložené dokumenty neobnoví, správce restartování dočasné soubory zahodí.

> [!NOTE]
> Můžete přepsat výchozí chování správce restartování pro ukládání dat a restartování aplikace.

Ve výchozím nastavení podporují aplikace knihovny MFC vytvořené pomocí průvodce projektem v sadě Visual Studio správce restartování při spuštění aplikací v počítači s operačním systémem Windows Vista nebo novějším. Pokud nechcete, aby aplikace podporovala správce restartování, můžete správce restartování zakázat v novém průvodci projektem.

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Přidání podpory správce restartování do existující aplikace

1. Otevřete existující aplikaci knihovny MFC v sadě Visual Studio.

1. Otevřete zdrojový soubor hlavní aplikace. Ve výchozím nastavení se jedná o soubor CPP, který má stejný název jako aplikace. Například hlavní zdrojový soubor aplikace pro MyProject je MyProject.cpp.

1. Najděte konstruktor pro hlavní aplikaci. Například pokud je projekt MyProject, konstruktor je `CMyProjectApp::CMyProjectApp()`.

1. Přidejte následující řádek kódu do konstruktoru.

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. Ujistěte `InitInstance` se, že metoda `InitInstance` aplikace volá svou nadřazenou `CWinAppEx::InitInstance`metodu: [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) nebo . Metoda `InitInstance` je zodpovědná za kontrolu *m_dwRestartManagerSupportFlags* parametru.

1. Zkompilujte a spusťte aplikaci.

## <a name="see-also"></a>Viz také

[CDataRecoveryHandler – třída](../mfc/reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[CWinApp – třída](../mfc/reference/cwinapp-class.md)<br/>
[CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[Cdocument::Událost OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)
