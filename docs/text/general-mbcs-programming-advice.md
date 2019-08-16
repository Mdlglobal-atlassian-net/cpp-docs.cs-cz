---
title: Obecné rady k programování se znakovou sadou MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 887387220105614eb3257f008ec601a6fc0adc18
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491187"
---
# <a name="general-mbcs-programming-advice"></a>Obecné rady k programování se znakovou sadou MBCS

Použijte následující tipy:

- Pro flexibilitu použijte makra run-time, například `_tcschr` a `_tcscpy` , pokud je to možné. Další informace naleznete v tématu [Mapování obecného textu v Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

- K získání informací o aktuální znakové `_getmbcp` stránce použijte funkci run-time jazyka C.

- Nepoužívejte znovu prostředky řetězců. V závislosti na cílovém jazyce může mít daný řetězec při překladu jiný význam. Například "soubor" v hlavní nabídce aplikace se může přeložit odlišně od řetězce "soubor" v dialogovém okně. Pokud potřebujete použít více než jeden řetězec se stejným názvem, použijte pro každou z nich různá ID řetězců.

- Můžete chtít zjistit, jestli je vaše aplikace spuštěná v operačním systému s podporou znakové sady MBCS. Provedete to tak, že nastavíte příznak při spuštění programu. nespoléhejte na volání rozhraní API.

- Při navrhování dialogových oken povolte na konci statického textu ovládací prvky pro překlad znakové sady MBCS přibližně 30% dodatečného místa.

- Při výběru písem pro aplikaci buďte opatrní, protože některá písma nejsou k dispozici ve všech systémech.

- Při výběru písma pro dialogová okna použijte [MS Shell Dlg](/windows/win32/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) místo MS Sans Serif nebo Helvetica. Před vytvořením dialogového okna je systém MS Shell Dlg nahrazen správným písmem. Pomocí programu MS Shell Dlg zajistíte, aby byly všechny změny v operačním systému, které se budou s tímto písmem řešit, automaticky dostupné. (MFC nahrazuje program MS Shell Dlg pomocí DEFAULT_GUI_FONT nebo systémových písem ve Windows 95, Windows 98 a Windows NT 4, protože tyto systémy nezpracovávají správně program MS Shell.)

- Při návrhu aplikace se rozhodněte, které řetězce lze lokalizovat. Pokud je to v nejistém případě, předpokládá se, že jakýkoli daný řetězec bude lokalizovaný. V takovém případě Nekombinujte řetězce, které mohou být lokalizovány do těch, které nemohou.

## <a name="see-also"></a>Viz také:

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Inkrementace a dekrementace ukazatelů](../text/incrementing-and-decrementing-pointers.md)
