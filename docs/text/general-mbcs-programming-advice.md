---
title: Obecné rady k programování se znakovou sadou MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 31c17d6d6dee49f75f5cd8f84aa0690e649aa509
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410671"
---
# <a name="general-mbcs-programming-advice"></a>Obecné rady k programování se znakovou sadou MBCS

Použijte následující tipy:

- Zajišťuje tak flexibilitu, použijte makra za běhu `_tcschr` a `_tcscpy` Pokud je to možné. Další informace najdete v tématu [mapování obecného textu v souboru tchar.h](../text/generic-text-mappings-in-tchar-h.md).

- Použití za běhu C `_getmbcp` funkce získáte informace o aktuální znakové stránce.

- Nepoužívejte opakovaně řetězcové prostředky. V závislosti na cílový jazyk daný řetězec může mít jiný význam při překladu. Hlavní nabídky "Soubor" na aplikace může například překládat odlišně od řetězcem "File" v dialogovém okně. Pokud potřebujete použít více než jeden řetězec se stejným názvem, použijte jiný řetězec ID pro každý.

- Můžete chtít zjistit, jestli vaše aplikace běží v operačním systému povolena znakové sady MBCS. Uděláte to tak, nastavte příznak, který při spuštění programu; Nespoléhejte na volání rozhraní API.

- Při navrhování dialogových oknech, povolte přibližně 30 % mezery na konci ovládacích prvků statického textu pro překlad znakové sady MBCS.

- Buďte opatrní při výběru písma pro vaši aplikaci, protože se některá písma nejsou k dispozici na všech systémech.

- Při výběru písma pro dialogová okna, použijte [MS Shell Dlg](/windows/desktop/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) místo Serif MS sítě SAN nebo Helvetica. Před vytvořením dialogové okno se nahradí MS Shell Dlg s použitím správného písma v systému. Použití MS Shell Dlg zajistí, že všechny změny v operačním systému se toto písmo budou automaticky dostupné. (MFC nahradí MS Shell Dlg DEFAULT_GUI_FONT nebo systémové písmo na Windows 95, Windows 98 a Windows NT 4 vzhledem k tomu, že tyto systémy nezpracuje MS Shell Dlg správně.)

- Při návrhu aplikace, rozhodněte, které řetězce může být lokalizována. Pokud máte pochybnosti, se předpokládá, že bude lokalizovaný libovolný daný řetězec. V důsledku toho Nekombinujte řetězce, které může být lokalizována s těmi, které nelze.

## <a name="see-also"></a>Viz také:

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Inkrementace a dekrementace ukazatelů](../text/incrementing-and-decrementing-pointers.md)
