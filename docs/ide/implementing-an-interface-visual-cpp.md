---
title: Implementace rozhraní
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: bb1db35e269ef884f3ebdf4564d8f0a3e579db50
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509508"
---
# <a name="implement-an-interface"></a>Implementace rozhraní

Chcete-li implementovat rozhraní, je nutné vytvořit projekt jako aplikaci ATL COM nebo jako aplikaci MFC, která obsahuje podporu knihovny ATL. [Průvodce projektem ATL](../atl/reference/atl-project-wizard.md) můžete použít k vytvoření aplikace ATL nebo k [Přidání objektu ATL do aplikace MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) pro implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

Po vytvoření projektu, aby bylo možné implementovat rozhraní, je nutné nejprve přidat objekt ATL. Seznam průvodců, které přidávají objekty do projektu knihovny ATL, naleznete v tématu [Přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) .

> [!NOTE]
> Průvodce nepodporuje dialogová okna knihovny ATL, webové služby XML využívající knihovny ATL, objekty výkonu ani čítače výkonu.

Pokud [přidáte ovládací prvek ATL](../atl/reference/adding-an-atl-control.md), můžete určit, zda implementovat výchozí rozhraní. Výchozí rozhraní jsou uvedena na stránce [rozhraní](../atl/reference/interfaces-atl-control-wizard.md) tohoto průvodce a definovány v atlcom. h.

Po přidání objektu nebo ovládacího prvku můžete implementovat další rozhraní umístěná v libovolné dostupné knihovně typů pomocí Průvodce implementací rozhraní.

Pokud přidáváte nové rozhraní, musíte ho přidat ručně do souboru. idl projektu. Další informace najdete v tématu [Přidání nového rozhraní v projektu ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md).

**Implementace rozhraní:**

1. V Zobrazení tříd klikněte pravým tlačítkem myši na název třídy pro váš objekt ATL.

1. V místní nabídce zvolte možnost **Přidat** a potom kliknutím na možnost **implementovat rozhraní** zobrazte [Průvodce implementací rozhraní](#implement-interface-wizard).

1. Vyberte rozhraní, která chcete implementovat z odpovídajících knihoven typů a vyberte **Dokončit**.

1. V Zobrazení tříd rozbalte uzel základy a rozhraní objektu, abyste viděli rozhraní, které jste implementovali. Pak rozbalte uzel rozhraní, abyste viděli dostupné vlastnosti, metody a události.

   > [!NOTE]
   > Můžete také použít [Prohlížeč objektů](/visualstudio/ide/viewing-the-structure-of-code) k prohlédnutí členů rozhraní.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce implementací rozhraní](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>Průvodce implementací rozhraní

Tento průvodce implementuje rozhraní pro objekt modelu COM. Implementace mnoha rozhraní jsou součástí knihoven COM, které jsou k dispozici v aplikaci Visual Studio a ve Windows. Implementace rozhraní je přidružena k objektu při vytvoření instance daného objektu. Poskytuje také služby, které objekt nabízí.

Diskuzi o rozhraních a implementacich naleznete v tématu [rozhraní a implementace rozhraní](/windows/win32/com/interfaces-and-interface-implementations) v Windows SDK.

- **Implementovat rozhraní z**

  Určuje umístění knihovny typů, ze které se vytvoří rozhraní.

  |Možnost|Popis|
  |------------|-----------------|
  |**Projekt**|Knihovna typů je součástí projektu.|
  |**Rejstříku**|Knihovna typů je registrována v systému. Registrované knihovny typů jsou uvedeny v seznamu **Dostupné knihovny typů**.|
  |**File**|Knihovna typů není nutně registrována v systému, ale je uložena v souboru. Zadejte umístění souboru do pole **umístění**.|

- **Dostupné knihovny typů**

  Zobrazí dostupné knihovny typů obsahující definice rozhraní, které můžete implementovat. Pokud zvolíte možnost **soubor** v části **implementovat rozhraní z**, toto políčko není k dispozici pro změnu.

- **Poloha**

  Zobrazí umístění aktuálně vybrané knihovny typů v seznamu **Dostupné knihovny typů** . Pokud jste vybrali možnost **soubor** v části **implementovat rozhraní z**, vyberte tlačítko se třemi tečkami a vyhledejte soubor obsahující knihovnu typů, která se má použít.

- **Rozhraní**

  Zobrazuje rozhraní, jejichž definice jsou uloženy v aktuálně vybrané knihovně typů v poli **Dostupné knihovny typů** .

  > [!NOTE]
  > Rozhraní, která mají stejný název jako již implementované vybraným objektem, se nezobrazí v poli **rozhraní** .

  |Tlačítko přenos|Popis|
  |---------------------|-----------------|
  |**>**|Přidá do seznamu rozhraní **implementace** aktuálně vybraný název rozhraní v seznamu **rozhraní** .|
  |**>>**|Přidá do seznamu **rozhraní implementace** všechny názvy rozhraní, které jsou k dispozici v seznamu **rozhraní** .|
  |**\<**|Odebere název rozhraní aktuálně vybraného v seznamu **Implement rozhraní** .|
  |**\<\<**|Odebere všechny názvy rozhraní, které jsou aktuálně uvedeny v seznamu **Implement rozhraní** .|

- **Implementovat rozhraní**

  Zobrazuje názvy rozhraní, která jste vybrali pro implementaci na vašem objektu.

  > [!NOTE]
  > Pokud zahrnete více než jedno rozhraní, které je odvozeno z `IDispatch`nástroje, nebo pokud se pokusíte implementovat rozhraní, které je odvozeno z jiného rozhraní již na vaší třídě, je nutné položky COM_MAP jednoznačně určit. Další informace najdete v tématu [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2).
