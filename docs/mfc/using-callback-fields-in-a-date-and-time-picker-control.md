---
title: Použití polí zpětného volání v ovládacím prvku pro výběr data a času
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 874f73df3dda3a720d4346ae3fb0136c662221db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403578"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Použití polí zpětného volání v ovládacím prvku pro výběr data a času

Kromě standardní formát znaků, které definují polích pro výběr data a času můžete přizpůsobit výstup tak, že zadáte určité části řetězci vlastního formátu jako pole zpětného volání. Chcete-li deklarovat pole zpětného volání, zahrnují jeden nebo více znaků "X" (ASCII kódu 88) kdekoli v těle formátovací řetězec. Například následující řetězec "" Dnes je: "yy" / "MM" / "dd" (den "X") ""způsobí, že datum a čas pro výběr ovládací prvek zobrazuje aktuální hodnotu jako rok a měsíc, datum a nakonec den v roce.

> [!NOTE]
>  Počet bezpodmínečný ve zpětném volání pole neodpovídá počtu znaků, které se zobrazí.

Možné rozlišit mezi více polí zpětného volání ve vlastním řetězcem opakováním znak "X". Proto formátovací řetězec "XXddddMMMdd", "yyyXXX" obsahuje dvě pole jedinečný zpětné volání "XX" a "XXX".

> [!NOTE]
>  Pole zpětného volání jsou považovány za platné pole, takže vaše aplikace musí být připravena ke zpracování zpráv s oznámením DTN_WMKEYDOWN.

Implementace pole zpětného volání v ovládacím prvku vaše data a času výběr se skládá ze tří částí:

- Inicializuje řetězec vlastního formátu

- Zpracování dtn_formatquery – oznámení

- Zpracování dtn_format – oznámení

## <a name="initializing-the-custom-format-string"></a>Inicializuje řetězec vlastního formátu

Inicializuje vlastní řetězec voláním `CDateTimeCtrl::SetFormat`. Další informace najdete v tématu [pomocí vlastní formátovací řetězce datum a čas ovládací prvek výběru](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Společné místo, kde můžete nastavit vlastní formátovací řetězec je v `OnInitDialog` funkce třídy obsahující dialogové okno nebo `OnInitialUpdate` funkce třídy obsahující zobrazení.

## <a name="handling-the-dtnformatquery-notification"></a>Zpracování dtn_formatquery – oznámení

Když ovládací prvek analyzuje řetězec formátu, pole zpětného volání, zaznamená aplikace odesílá atributu DTN_FORMAT a dtn_formatquery – oznámení. Řetězec pole zpětného volání je součástí oznámení, aby mohl určit, které pole zpětného volání je dotazována.

Dtn_formatquery – oznámení, přijde načíst maximální povolenou velikost v pixelech řetězce, který se zobrazí v aktuálním poli zpětného volání.

Chcete-li tuto hodnotu vypočítat správně, je nutné vypočítat výšku a šířku řetězce na pole, nahradí pomocí ovládacího prvku zobrazení písma. Skutečné výpočtu řetězce je snadno nastavit pomocí volání [GetTextExtentPoint32](/windows/desktop/api/wingdi/nf-wingdi-gettextextentpoint32a) funkci Win32. Jakmile velikost je určena, předejte hodnotu zpět do aplikace a obslužné rutiny ukončení.

V následujícím příkladu je jedna z metod poskytnutí velikost řetězce zpětného volání:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Jakmile byla vypočtena velikost aktuálního pole zpětného volání, je třeba zadat hodnotu pro pole. To se provádí v obslužné rutině dtn_format – oznámení.

## <a name="handling-the-dtnformat-notification"></a>Zpracování dtn_format – oznámení

Dtn_format – oznámení aplikací slouží k vyžádání řetězec znaků, která bude nahrazena. Následující příklad ukazuje jednu metodu možné:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  Ukazatel **NMDATETIMEFORMAT** je přetypováním první parametr obslužné rutiny oznámení na správný typ. nalezena.

## <a name="see-also"></a>Viz také:

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
