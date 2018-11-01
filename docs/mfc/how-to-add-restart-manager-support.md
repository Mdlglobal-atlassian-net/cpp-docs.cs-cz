---
title: 'Postupy: Přidání podpory správce restartování'
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 77267cdad1fa976d73381ca798ca5002c09dc7ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565130"
---
# <a name="how-to-add-restart-manager-support"></a>Postupy: Přidání podpory správce restartování

Správce restartování je funkce přidána do Visual Studio pro Windows Vista nebo novější operační systémy. Správce restartování přidává podporu pro vaši aplikaci, pokud se neočekávaně zavře nebo restartuje. Chování správce restartování závisí na typu aplikace. Pokud vaše aplikace je editoru dokumentů, správce restartování povolené automaticky uložit stav aplikace a obsah otevřených dokumentů a restartuje po neočekávaném ukončení aplikace. Pokud vaše aplikace není editoru dokumentů, restartuje správce restartování aplikace, ale ve výchozím nastavení ho Nejde uložit stav aplikace.

Po restartování aplikace zobrazí dialogové okno úloh, pokud je aplikace kódování Unicode. Pokud se jedná o aplikaci ANSI, aplikace se zobrazí okno se zprávou Windows. V tomto okamžiku uživatel rozhodne, zda se má obnovit automaticky uložené dokumenty. Pokud uživatel neobnovuje automaticky uložené dokumenty, správce restartování odstraní dočasné soubory.

> [!NOTE]
>  Můžete přepsat výchozí chování správce restartování pro ukládání dat a restartování aplikace.

Ve výchozím nastavení MFC aplikace vytvořené pomocí Průvodce projektu v sadě Visual Studio podpory správce restartování při spuštění aplikace na počítači s Windows Vista nebo novějším operačním systémem. Pokud nechcete, aby aplikace pro potřeby podpory správce restartování, můžete zakázat správce restartování v Průvodci vytvořením projektu.

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Přidání podpory správce restartování do existující aplikace

1. V sadě Visual Studio otevřete existující aplikaci MFC.

1. Otevřete zdrojový soubor pro hlavní aplikaci. Ve výchozím nastavení to je soubor .cpp, který má stejný název jako vaše aplikace. Například hlavní aplikace zdrojový soubor pro MyProject je MyProject.cpp.

1. Najdete konstruktoru pro hlavní aplikaci. Například pokud váš projekt je MyProject, konstruktor je `CMyProjectApp::CMyProjectApp()`.

1. Přidejte následující řádek kódu do konstruktoru.

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. Ujistěte se, že `InitInstance` metoda aplikace volá svého nadřazeného objektu `InitInstance` metoda: [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) nebo `CWinAppEx::InitInstance`. `InitInstance` Metoda je odpovědná za kontrolu *m_dwRestartManagerSupportFlags* parametru.

1. Kompilace a spuštění aplikace.

## <a name="see-also"></a>Viz také

[CDataRecoveryHandler – třída](../mfc/reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[CWinApp – třída](../mfc/reference/cwinapp-class.md)<br/>
[CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)

