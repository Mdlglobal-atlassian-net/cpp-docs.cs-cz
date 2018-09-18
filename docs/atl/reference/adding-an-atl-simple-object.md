---
title: Přidání jednoduchého objektu ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.adding.atl
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1347fcebc6a3793cbe63ae356f7f9d2e03742cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109766"
---
# <a name="adding-an-atl-simple-object"></a>Přidání jednoduchého objektu ATL

Chcete-li do svého projektu přidat objekt ATL (knihovnu Active Template Library), váš projekt musí být vytvořen jako aplikace ATL nebo MFC aplikaci, která obsahuje podpory knihovny ATL Můžete použít [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

Můžete definovat rozhraní modelu COM pro nový objekt knihovny ATL při vytvoření, nebo je přidat později pomocí [implementovat rozhraní](../../ide/implement-interface-wizard.md) příkazu v místní nabídce Zobrazení tříd.

### <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Přidání jednoduchého objektu ATL do projektu knihovny ATL modelu COM

1. V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat jednoduchý objekt knihovny ATL.

2. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

3. V [přidat třídu](../../ide/add-class-dialog-box.md) dialogové okno, v podokně šablon, klikněte na tlačítko **jednoduchý objekt knihovny ATL**a potom klikněte na tlačítko **otevřít** zobrazíte [ATL Simple Object Wizard](../../atl/reference/atl-simple-object-wizard.md).

4. Nastavit další možnosti pro váš projekt na [možnosti](../../atl/reference/options-atl-simple-object-wizard.md) stránky Průvodce jednoduchým objektem ATL.

5. Klikněte na tlačítko **Dokončit** pro přidání objektu do projektu.

## <a name="see-also"></a>Viz také

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání nového rozhraní projektu ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Přidání bodů připojení objektu](../../atl/adding-connection-points-to-an-object.md)<br/>
[Přidání metody](../../ide/adding-a-method-visual-cpp.md)<br/>
[Třída knihovny MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Přidání generické třídy jazyka C++](../../ide/adding-a-generic-cpp-class.md)

