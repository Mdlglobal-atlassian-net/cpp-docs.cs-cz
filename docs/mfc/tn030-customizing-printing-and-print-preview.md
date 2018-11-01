---
title: 'TN030: Přizpůsobení tisku a tiskového náhledu'
ms.date: 06/28/2018
f1_keywords:
- vc.print
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
ms.openlocfilehash: 09938c5cec2812998d5e76e15154754ad3ac3e0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667903"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030: Přizpůsobení tisku a tiskového náhledu

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje proces přizpůsobení tisku a tiskového náhledu a účely procedury zpětného volání používané v `CView` a zpětné volání rutiny a členské funkce `CPreviewView`.

## <a name="the-problem"></a>Problém

Knihovna MFC poskytuje kompletní řešení pro většinu tisk a náhled tisku potřebuje. Ve většině případů je potřeba mít možnost Tisk a náhled zobrazení trochu další kód. Ale způsoby optimalizovat tisk, které vyžadují značné úsilí ze strany vývojáře a některých aplikací nutné přidat prvky konkrétní uživatelského rozhraní do režimu náhledu.

## <a name="efficient-printing"></a>Efektivní tisk

Když aplikace knihovny MFC vytiskne pomocí standardních metod, Windows určí, že všechna volání rozhraní grafického zařízení (GDI) výstup v paměti metasouboru. Když `EndPage` je volána, hraje Windows metafile jednou pro každé fyzické pásmo vyžadující tiskárny pro tisk jednu stránku. Během této vykreslování GDI často dotazuje postupu přerušit určilo, zda by měl pokračovat. Postup zrušení obvykle umožňuje zprávy zpracovat tak, aby uživatel se může přerušit tiskových úloh používajících dialogové okno Tisk.

Bohužel to může zpomalit proces tisku. Pokud tisk ve vaší aplikaci musí být rychlejší, než lze dosáhnout pomocí standardní postup, musíte implementovat řazení do pásem ruční.

## <a name="print-banding"></a>Tisk řazení do pásem

Aby bylo možné ručně pásmo, je nutné znovu implementovat smyčka tisku tak, aby `OnPrint` je volána více než jednou na jedné stránce (jednou za band). Tisk smyčky je implementována v `OnFilePrint` funkce v viewprnt.cpp. Ve vaší `CView`-odvozené třídy, přetížení této funkce tak, aby položku mapy zpráv pro zpracování tisku příkazu volá funkci tisku. Kopírovat `OnFilePrint` rutiny a změnit tisku smyčky implementovat řazení do pásem. Pravděpodobně budete chtít předat řazení do pásem obdélník tisk funkce, takže je možné optimalizovat podle části tištěnou stránku výkresu.

Za druhé, je nutné často volat `QueryAbort` při kreslení pásmo. V opačném případě nebude zavolána procedury Abort a uživatel bude schopen tiskovou úlohu zrušit.

## <a name="print-preview-electronic-paper-with-user-interface"></a>Náhled tisku: Elektronické dokument s uživatelským rozhraním

Náhled, v podstatě se pokusí změnit zobrazení do emulaci tiskárnu. Ve výchozím nastavení klientské oblasti hlavního okna slouží k zobrazení jedné nebo dvou stránek plně v rámci okna. Uživatel je schopen přiblížení oblasti stránky a prohlédněte si ho podrobněji. S dodatečnou podporou může uživatel i oprávnění k provádění úprav v režimu náhledu.

## <a name="customizing-print-preview"></a>Přizpůsobení náhledu tisku

Tato poznámka zabývá pouze jeden aspekt úpravy náhledu tisku: Přidání uživatelského rozhraní do režimu náhledu. Další změny, ale ta tyto změny jsou mimo rozsah této diskuse.

## <a name="to-add-ui-to-the-preview-mode"></a>Přidání uživatelského rozhraní do režimu náhledu

1. Odvodit třídu zobrazení z `CPreviewView`.

2. Přidejte obslužné rutiny příkazů pro funkce uživatelského rozhraní, které očekáváte.

3. Pokud přidáváte visual aspekty na obrazovce, má přednost před `OnDraw` a provádět výkresu po volání `CPreviewView::OnDraw`.

## <a name="onfileprintpreview"></a>OnFilePrintPreview

Toto je obslužná rutina příkazu pro zobrazení náhledu tisku. Jeho výchozí implementace je:

```cpp
void CView::OnFilePrintPreview()
{
    // In derived classes, implement special window handling here
    // Be sure to Unhook Frame Window close if hooked.

    // must not create this on the frame. Must outlive this function
    CPrintPreviewState* pState = new CPrintPreviewState;

    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR, this,
        RUNTIME_CLASS(CPreviewView), pState))
    {
        // In derived classes, reverse special window handling
        // here for Preview failure case

        TRACE0("Error: DoPrintPreview failed");
        AfxMessageBox(AFX_IDP_COMMAND_FAILURE);
        delete pState;  // preview failed to initialize, delete State now
    }
}
```

`DoPrintPreview` v hlavním podokně aplikace budou skrývat. Ovládací pruhy, jako je například stavového řádku, se můžou ukládat zadáním do pState ->*dwStates* člena (to je bitová maska a bity pro jednotlivé ovládací pruhy jsou definovány AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR)). -> Okna pState*nIDMainPane* je okno, které budou automaticky skrytá a reshown. `DoPrintPreview` potom vytvoří panel tlačítek pro standardní uživatelské rozhraní ve verzi Preview. V případě potřeby se speciální okno zpracování, například za účelem skrýt nebo zobrazit ostatní okna, které by mělo být provedeno před `DoPrintPreview` je volána.

Ve výchozím nastavení až se dokončí náhledu tisku, vrátí ovládací pruhy do jejich původního stavu a v hlavním podokně na viditelný. V případě potřeby je zvláštní zacházení, je třeba jej provést v přepsání `EndPrintPreview`. Pokud `DoPrintPreview` selže, také poskytují zvláštní zpracování.

DoPrintPreview je volána pomocí:

- ID prostředku šablony dialogového okna pro panel nástrojů ve verzi preview.

- Ukazatel na zobrazení nedokázala náhledu tisku.

- Run-time třída třídy zobrazení ve verzi Preview. To dynamicky vytvoří se v DoPrintPreview.

- CPrintPreviewState ukazatele. Všimněte si, že CPrintPreviewState strukturu (nebo odvozené struktury, pokud aplikace potřebuje více stavů zachovaný) musí *není* vytvořené v rámci. Tato struktura musí překonat, dokud se nazývá EndPrintPreview DoPrintPreview je nemodální.

  > [!NOTE]
  > V případě potřeby oddělená zobrazení nebo zobrazení třídy pro podporu tisku ukazatel na tento objekt předat jako druhý parametr.

## <a name="endprintpreview"></a>EndPrintPreview

Tomu se říká ukončení režimu náhledu. Často je třeba přejít na stránku v dokumentu, který byl naposledy zobrazených v náhledu tisku. `EndPrintPreview` je pravděpodobné, aplikace, které provedete. -> PInfo*m_nCurPage* člen stránku, která byla zobrazená naposledy (nejvíce vlevo, pokud se zobrazí dvě stránky) a pomocného parametru, kde na stránce uživatel se chtěli byste je ukazatel. Protože strukturu zobrazení vaší aplikace Neznámý rozhraní Framework, je nutné zadat kód, který přesunout na zvolený bod.

By měl provádět většinu akcí před voláním `CView::EndPrintPreview`. Toto volání obrátí účinek `DoPrintPreview` a odstraní pView primárního řadiče domény a pInfo.

```cpp
// Any further cleanup should be done here.
CView::EndPrintPreview(pDC, pInfo, point, pView);
```

## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup

Toto musí být mapována pro položku nabídky Nastavení tisku. Ve většině případů není nutné přepsat implementaci.

## <a name="page-nomenclature"></a>Terminologie stránce

Dalším problémem je, že stránkování a pořadí. Pro aplikace typu jednoduchý textový procesor jedná se o jednoduchý problém. Většina systémů náhledu se předpokládá, že každý tištěném odpovídá jedné stránky v dokumentu.

Při pokusu o poskytují generalizovaný řešení, je potřeba uvážit několik věcí. Představte si CAD systému. Uživatel nemá výkresu, která zahrnuje několik E-velikost listů. Na E-velikosti (nebo menší, škálování) zapisovače, stránkování bude podobat jednoduchý případ. Ale na laserová tiskárna, tisk 16 stránky A velikost na list, co náhledu tisku vezměte v úvahu "page"

Jak uvádí úvodní odstavec náhled funguje jako tiskárna. Proto uživateli se zobrazí, co by pocházejí z určité tiskárny, který je vybrán. Záleží zobrazení a určit, jaké image je vytištěna na každé stránce.

Řetězce popisu stránky v `CPrintInfo` struktura poskytuje způsob zobrazení číslo stránky na uživatele, pokud může být reprezentován jako jedno číslo na stránku (stejně jako v "Stránka 1" nebo "stránkách 1-2"). Tento řetězec se používá výchozí implementace `CPreviewView::OnDisplayPageNumber`. V případě potřeby jiným zobrazením jeden mohou přepsat tuto virtuální funkce poskytnout, například "List1, oddíly A, B".

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
