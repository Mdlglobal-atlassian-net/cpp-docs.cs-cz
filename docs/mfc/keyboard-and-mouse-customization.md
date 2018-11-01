---
title: Přizpůsobení klávesnice a myši
ms.date: 11/04/2016
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 8bb685974ed4020611ffe275ba504951d132afac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487384"
---
# <a name="keyboard-and-mouse-customization"></a>Přizpůsobení klávesnice a myši

MFC umožňuje uživateli aplikace přizpůsobit, jak zpracovává klávesnice a myši. Uživatel může upravit vstup z klávesnice přiřazením klávesové zkratky pro příkazy. Uživatele můžete také upravit vstup myši tak, že vyberete příkaz, který má být spuštěn při poklepání uvnitř konkrétní windows aplikace. Toto téma vysvětluje, jak přizpůsobit vstup pro vaši aplikaci.

V **přizpůsobení** dialogové okno, uživatel může změnit vlastní ovládací prvky pro myš a klávesnici. Chcete-li zobrazit toto dialogové okno, uživatel odkazuje na **vlastní** na **zobrazení** nabídky a pak klikne na tlačítko **panely nástrojů a ukotvení**. V dialogovém okně kliknutí buď **klávesnice** kartu nebo **myši** kartu.

## <a name="keyboard-customization"></a>Přizpůsobení klávesnice

Je vidět na následujícím obrázku **klávesnice** karty **přizpůsobení** dialogové okno.

![Na kartě klávesnice v dialogovém okně přizpůsobení](../mfc/media/mfcnextkeyboardtab.png "mfcnextkeyboardtab") kartu přizpůsobení klávesnice

Uživatel pracuje se na kartě klávesnice přiřazení jednoho nebo více klávesových zkratek k příkazu. Dostupné příkazy jsou uvedené na levé straně karty. Uživatel může vybrat všechny dostupné příkazy v nabídce. Jenom příkazy nabídky můžou být spojené s klávesové zkratky. Poté, co uživatel zadá nového zástupce **přiřadit** aktivuje tlačítko. Po kliknutí na toto tlačítko, přidruží aplikaci tato zkratka vybraný příkaz.

V seznamu v pravém sloupci jsou uvedeny všechny aktuálně přiřazené klávesové zkratky. Uživatele můžete také vybrat jednotlivé klávesové zkratky a je odebrat nebo resetovat všechna mapování pro aplikaci.

Pokud chcete zajistit podporu tohoto vlastního nastavení v aplikaci, musíte vytvořit [ckeyboardmanager –](../mfc/reference/ckeyboardmanager-class.md) objektu. Chcete-li vytvořit `CKeyboardManager` objektu, zavolejte funkci [CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager). Tato metoda vytvoří a inicializuje správce klávesnice. Pokud vytvoříte klávesnice správce ručně, můžete stále musí volat `CWinAppEx::InitKeyboardManager` inicializovat ji.

Pokud použijete průvodce k vytvoření aplikace, průvodce se inicializace správce klávesnice. Po aplikaci inicializuje správce klávesnice, přidá rozhraní **klávesnice** záložku **přizpůsobení** dialogové okno.

## <a name="mouse-customization"></a>Vlastní nastavení myši

Je vidět na následujícím obrázku **myši** karty **přizpůsobení** dialogové okno.

![Kartu Myš v dialogovém okně přizpůsobení](../mfc/media/mfcnextmousetab.png "mfcnextmousetab") myši přizpůsobení karty

Uživatel pracuje se na této kartě přiřadit nabídky příkazu myši dvakrát klikněte na akci. Uživatel vybere zobrazení na levé straně okna a potom pomocí ovládacích prvků na pravé straně přidružit akce dvakrát klikněte na příkaz. Když uživatel klikne na tlačítko **Zavřít**, aplikace provede přidružený příkaz pokaždé, když uživatel poklepe kdekoli v zobrazení.

Ve výchozím nastavení přizpůsobení myši není povoleno při vytváření aplikace s použitím průvodce.

#### <a name="to-enable-mouse-customization"></a>Povolení přizpůsobení myši

1. Inicializace [cmousemanager –](../mfc/reference/cmousemanager-class.md) objektu voláním [CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager).

1. Získat ukazatel myši manager pomocí [CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager).

1. Přidání zobrazení do správce myši s použitím [CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview) metody. To lze proveďte pro každé zobrazení, které chcete přidat do správce myši.

Po aplikaci inicializuje správce myši, přidá rozhraní **myši** záložku **vlastní** dialogové okno. Pokud nemůžete přidat žádné zobrazení, na kartě způsobí neošetřenou výjimku. Jakmile vytvoříte seznam zobrazení, **myši** karta je k dispozici pro uživatele.

Při přidání nové zobrazení pro správce myši jí přiřadit jedinečné ID. Pokud chcete zajistit podporu myši přizpůsobení okna, je nutné zpracovat zprávu WM_LBUTTONDBLCLICK a volání [CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkce. Při volání této funkce je jeden z parametrů Identifikátor pro toto okno. Je odpovědností programátorovi, aby udržovat přehled o čísla ID a objekty, které jsou k nim má přiřazené.

## <a name="security-concerns"></a>Zajištění zabezpečení

Jak je popsáno v [uživatelem definované nástroje](../mfc/user-defined-tools.md), uživatel může přidružit k ID uživatelsky definovaného nástroje dvakrát klikněte na události. Když uživatel poklepe zobrazení, aplikace vyhledá uživatelský nástroj, který odpovídá přidružené ID. Pokud aplikace zjistí vhodný nástroj, spustí nástroj. Pokud aplikace nelze najít vhodný nástroj, odešle wm_command – zprávy s ID do zobrazení, která byla dvojitému kliknutí.

Vlastní nastavení se ukládají v registru. Úpravou registru můžete nahradit útočník platné nástroj ID uživatele libovolný příkaz. Když uživatel poklepe zobrazení, zobrazení zpracuje příkaz, který útočník vysazeny. To může způsobit neočekávané a potenciálně nebezpečné chování.

Kromě toho tento druh útoku může obejít ochranu uživatelského rozhraní. Například předpokládejme, že aplikace má tisk je zakázán. To znamená, že ve svém uživatelském rozhraní **tisk** nabídky a tlačítko nejsou k dispozici. Obvykle to zabrání aplikaci v tisku. Ale pokud útočník upravit registr, uživatel může nyní může odeslat příkaz pro tisk přímo dvojitým kliknutím zobrazení bez použití prvky uživatelského rozhraní, které jsou k dispozici.

Pro ochranu proti tento druh útoku, přidejte kód pro vaše obslužná rutina příkazu aplikace ověřte, zda je příkazu platná před jeho provedením. Není závislý na uživatelské rozhraní pro příkazu zabrání v odesílání do aplikace.

## <a name="see-also"></a>Viz také

[Přizpůsobení pro prostředí MFC](../mfc/customization-for-mfc.md)<br/>
[CKeyboardManager – třída](../mfc/reference/ckeyboardmanager-class.md)<br/>
[CMouseManager – třída](../mfc/reference/cmousemanager-class.md)<br/>
[Vliv přizpůsobení na zabezpečení](../mfc/security-implications-of-customization.md)

