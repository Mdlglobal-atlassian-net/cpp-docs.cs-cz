---
title: "TN030: Přizpůsobení tisku a tiskového náhledu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.print
dev_langs:
- C++
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa11c30fb41630a5b293698fe3e69a80509f3f2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030: Přizpůsobení tisku a tiskového náhledu
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje proces přizpůsobení tisku a přehled tisku a účely procedury zpětného volání používané v `CView` a zpětného volání rutiny a členské funkce **CPreviewView**.  
  
## <a name="the-problem"></a>Problém  
 MFC poskytuje kompletní řešení pro většinu tisk a náhled tisku potřebuje. Ve většině případů je potřeba mít moct tisk a náhled zobrazení málo další kód. Ale existují způsoby, jak optimalizovat tisk, které vyžadují významné úsilí ze strany vývojář a některé aplikace je nutné přidat konkrétní prvky rozhraní na režim náhledu tisku.  
  
## <a name="efficient-printing"></a>Efektivní tisk  
 Pokud aplikace MFC vytiskne pomocí standardních metod, Windows určí, že všechna volání výstupu grafického rozhraní zařízení (GDI) metafile v paměti. Když `EndPage` je volána, Windows hraje metafile jednou pro každý fyzický vzdálené správy, který tiskárny vyžaduje, aby jednu stránku vytisknout. Během této vykreslování GDI často dotazuje Abort postup k určení, pokud by měly pokračovat. Postup zrušení obvykle umožňuje zprávy, které mají být zpracovány, takže uživatel může přerušit tiskových úloh používajících Tisk dialogové okno.  
  
 Bohužel se mohou zpomalit proces tisku. Pokud tisk ve vaší aplikaci musí být rychlejší než lze dosáhnout pomocí standardní techniky, musíte implementací ruční řazení do pásem.  
  
## <a name="print-banding"></a>Tisk řazení do pásem  
 Chcete-li ručně vzdálené, je nutné znovu implementovat tiskové smyčky tak, aby `OnPrint` je volat vícekrát, na stránce (jednou za band). Tiskové smyčky je implementována ve **OnFilePrint** funkce v viewprnt.cpp. Ve vašem `CView`-odvozené třídy, přetížení tuto funkci tak, aby položku mapy zpráv pro zpracování tiskových příkazu volá tiskové funkce. Kopírování **OnFilePrint** rutiny a změňte tiskovou smyčky implementovat řazení do pásem. Pravděpodobně budete také chtít předat řazení do pásem rámeček tiskové funkce, takže můžete optimalizovat kreslení podle části tisku stránky.  
  
 Druhý, musíte často volat `QueryAbort` při vykreslování vzdálené správy. Jinak hodnota nebude zavolána proces přerušit a uživatel nebude možné zrušit tiskové úlohy.  
  
## <a name="print-preview-electronic-paper-with-user-interface"></a>Náhledu tisku: Elektronické dokumentu s uživatelským rozhraním  
 Náhled, v podstatě pokusí změnit zobrazení do emulaci tiskárnu. Ve výchozím nastavení klientské oblasti hlavního okna se používá jedno nebo dvě stránky plně v rámci okna. Uživatel je schopen přiblížení oblast stránky zobrazíte podrobněji. S další podporu může uživatel i oprávnění k provádění úprav v režimu preview.  
  
## <a name="customizing-print-preview"></a>Přizpůsobení náhledu tisku  
 Tato poznámka zabývá pouze jeden aspekt úprav náhledu tisku: Přidání uživatelského rozhraní na režim náhledu. Je možné, ostatní změny, ale tyto změny jsou mimo rozsah toto pojednání.  
  
## <a name="to-add-ui-to-the-preview-mode"></a>Chcete-li přidat uživatelského rozhraní na režim náhledu  
  
1.  Odvození třídy z zobrazení **CPreviewView**.  
  
2.  Přidejte obslužné rutiny příkazů pro funkce uživatelského rozhraní, které očekáváte.  
  
3.  Pokud přidáváte visual aspekty do zobrazení, mají přednost před `OnDraw` a provádět výkresu po volání **CPreviewView::OnDraw.**  
  
## <a name="onfileprintpreview"></a>OnFilePrintPreview  
 Toto je obslužná rutina pro náhledu tisku. Jeho výchozí implementace je:  
  
```  
void CView::OnFilePrintPreview()  
{ *// In derived classes,
    implement special window handling here *// Be sure to Unhook Frame Window close if hooked.  
 *// must not create this on the frame. Must outlive this function  
    CPrintPreviewState* pState = new CPrintPreviewState;  
 
    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR,
    this,  
    RUNTIME_CLASS(CPreviewView),
    pState))  
 { *// In derived classes,
    reverse special window handling *// here for Preview failure case  
 
    TRACE0("Error: DoPrintPreview failed");

    AfxMessageBox(AFX_IDP_COMMAND_FAILURE);

 delete pState;      // preview failed to initialize, *// delete State now  
 }  
}  
```  
  
 **DoPrintPreview** se skrýt podokno hlavní aplikace. Ovládací pruhy, jako je například stavový řádek uchovávání může být zadáním v pState ->**dwStates** člen (to je bitová maska a jsou definovány bitů pro jednotlivé ovládací pruhy **AFX_CONTROLBAR_MASK**(AFX_IDW_MYBAR)). -> PState okno**nIDMainPane** okno, které budou automaticky skryté a reshown. **DoPrintPreview** pak vytvoří tlačítko panelu pro standardní uživatelské rozhraní Preview. V případě potřeby se speciální okno zpracování, například za účelem zobrazení nebo skrytí jiných windows, které je třeba provést před **DoPrintPreview** je volána.  
  
 Ve výchozím nastavení až se dokončí náhledu tisku, vrátí ovládací pruhy a stavy jejich původní hlavní podokno viditelné. V případě potřeby zvláštní zpracování by mělo být provedeno v přepsání **EndPrintPreview.** Pokud **DoPrintPreview** selže, zadejte také zvláštní zpracování.  
  
 DoPrintPreview je volán s:  
  
-   ID prostředku šablony dialogového okna pro panel nástrojů preview.  
  
-   Ukazatel na zobrazení provádět Tisk náhledu tisku.  
  
-   Run-time třída třídy zobrazení náhledu. To se dynamicky vytvoří DoPrintPreview.  
  
-   CPrintPreviewState ukazatel. Všimněte si, že strukturu CPrintPreviewState (nebo odvozené struktury, pokud aplikace potřebuje další stav zachovaná) musí *není* vytvořit rámec. Tato struktura musí překonat, dokud se nazývá EndPrintPreview DoPrintPreview je nemodální.  
  
    > [!NOTE]
    >  V případě potřeby samostatné zobrazení nebo zobrazení třídy pro podporu tisku ukazatel na tento objekt mají být předány jako druhý parametr.  
  
## <a name="endprintpreview"></a>EndPrintPreview  
 Tomu se říká ukončit režim náhledu tisku. Často je vhodné přejít na stránku v dokumentu, který byl naposledy zobrazené v náhledu tisku. **EndPrintPreview** aplikace příležitosti k tomu je. -> PInfo`m_nCurPage` člen je stránka, která se zobrazí poslední (nejvíce vlevo, pokud byly zobrazeny dvě stránky) a je ukazatel nápovědu, kde na stránku byl zúčastněné uživatele. Vzhledem k tomu, že strukturu zobrazení aplikace Neznámý do rozhraní, je nutné zadat kód, který chcete přesunout zvolený bod.  
  
 Byste měli provádět většinu akcí před voláním **CView::EndPrintPreview**. Toto volání obrátí důsledky **DoPrintPreview** a odstraní pView primárního řadiče domény a pInfo.  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC,
    pInfo,
    point,
    pView);
```  
  
## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup  
 Toto musí být mapován pro položku nabídky Nastavení tisku. Ve většině případů není potřeba přepsat implementace.  
  
## <a name="page-nomenclature"></a>Stránka klasifikace  
 Dalším problémem je, že číslování stránek a pořadí. Pro aplikace typ jednoduchého textového procesoru jedná se o snadný problém. Většina systémů náhledu tisku předpokládá, že každé vytištěné stránce odpovídá jedné stránky v dokumentu.  
  
 V pokusu o poskytují zobecněný řešení, jsou potřeba uvážit několik věcí. Představte si CAD systému. Uživatel má kreslení, které pokrývá několik E-velikost listů. Na E-velikosti (nebo menší, škálovat) stránkování by zapisovače, stejně jako jednoduchá. Ale na laserová tiskárna, tisk 16 A velikost stránky na list, co náhledu tisku vzít v úvahu "stránka"  
  
 Jako úvodní odstavec stavy, náhled funguje jako tiskárnu. Proto se uživateli zobrazí, co by být probuzeny z konkrétní tiskárny, který je vybraný. Je zobrazení a určit, jaké tisku na každé stránce.  
  
 Řetězec popisu stránky v `CPrintInfo` struktura poskytuje způsob zobrazení číslo stránky pro uživatele, pokud je to může být reprezentován jako jedno číslo na stránku (stejně jako "Stránka 1" nebo "stránky 1 – 2"). Tento řetězec používá výchozí implementaci **CPreviewView::OnDisplayPageNumber**. V případě potřeby jiným zobrazením může jeden virtuální funkci chcete zadat, například "Sheet1, A části B" přepsat.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

