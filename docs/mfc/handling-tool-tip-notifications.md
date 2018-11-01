---
title: Zpracování oznámení popisů tlačítek
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 973c4a12f3b3bdc91269736874b7193130290a76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548912"
---
# <a name="handling-tool-tip-notifications"></a>Zpracování oznámení popisů tlačítek

Pokud zadáte **TBSTYLE_TOOLTIPS** styl panelu nástrojů vytváří a spravuje ovládacím prvkem popis tlačítka nástroj. Popisku tlačítka je malého vyskakovacího okna, která obsahuje jeden řádek textu popisujícího tlačítka panelu nástrojů. Popis tlačítka je skrytý, povolí, jenom když uživatel umístí kurzor na tlačítka panelu nástrojů a ponechá ho existuje pro přibližně polovinu sekundy. Zobrazí se popis tlačítka téměř kurzor.

Předtím, než se zobrazí popis tlačítka, **TTN_NEEDTEXT** oznámení na panelu nástrojů nadřazenému oknu přijde načíst popisný text pro tlačítko. Pokud je okno vlastník panelu nástrojů `CFrameWnd` okno tipy jsou zobrazeny bez vyžadovalo zvláštní úsilí, protože nástroj `CFrameWnd` má výchozí obslužnou rutinu pro **TTN_NEEDTEXT** oznámení. Pokud okno panelu nástrojů vlastníka není odvozen od `CFrameWnd`, jako je například pole nebo formulář zobrazení dialogového okna, musíte přidat položku do mapy zprávu nadřazenému oknu a poskytnout obslužné rutina oznámení v mapování zprávy. Položka mapy zprávu nadřazenému oknu vypadá takto:

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>Poznámky

*memberFxn*<br/>
Členská funkce se volá, když pro toto tlačítko je nutné zadat text.

Všimněte si, že id popisku tlačítka je vždy 0.

Kromě **TTN_NEEDTEXT** oznámení, ovládacím prvkem popis tlačítka nástroje můžete odesílat následující oznámení do ovládacího prvku toolbar:

|Oznámení|Význam|
|------------------|-------------|
|**TTN_NEEDTEXTA**|Nástroj ovládacím prvkem popis tlačítka vyžaduje ASCII text (pouze Windows 95)|
|**TTN_NEEDTEXTW**|Text v kódu UNICODE (pouze Windows NT) vyžaduje nástroj ovládacím prvkem popis tlačítka|
|**TBN_HOTITEMCHANGE**|Označuje, že došlo ke změně aktivní (zvýrazněná) položka.|
|**NM_RCLICK –**|Označuje, že uživatel má pravým tlačítkem myši kliknou na tlačítko.|
|**TBN_DRAGOUT**|Označuje uživatel kliknul na tlačítko a přetáhnout ukazatel mimo tlačítko. Umožňuje aplikaci implementovat přetažení a přetažení z tlačítka panelu nástrojů. Při přijetí tohoto oznámení, aplikace bude začínat přetahování a operace odstranění.|
|**TBN_DROPDOWN –**|Označuje, že uživatel klikl tlačítko, které používá **TBSTYLE_DROPDOWN** style.|
|**TBN_GETOBJECT**|Označuje uživatel přesune ukazatel myši nad tlačítkem, který používá **TBSTYLE_DROPPABLE** style.|

Ukázkovou funkci obslužná rutina a další informace o povolení tipů nástrojů najdete v tématu [popisů tlačítek](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

