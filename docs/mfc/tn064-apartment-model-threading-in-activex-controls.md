---
title: 'TN064: Dělení na vlákna modelu apartment v ovládacích prvcích ActiveX'
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 2c6b9dd3ed244f7169e5055eebe7a34e3345e841
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513321"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Dělení na vlákna modelu apartment v ovládacích prvcích ActiveX

> [!NOTE]
>  Následující technická Poznámka nebyla od prvního zařazení do online dokumentace aktualizována. V důsledku toho mohou být některé postupy a témata neaktuální nebo nesprávné. Nejnovější informace najdete v tématu informace o tom, co je důležité v online katalogu dokumentace najít.

Tato technická Poznámka vysvětluje, jak v ovládacím prvku ActiveX povolit vláknování modelu apartment. Všimněte si, že dělení na vlákna modelu Apartment je podporované jenom C++ v vizuálů verze 4,2 nebo novější.

## <a name="what-is-apartment-model-threading"></a>Co je dělení na vlákna modelu apartment

Model Apartment je přístup k podpoře vložených objektů, jako jsou ovládací prvky ActiveX, v rámci vícevláknové aplikace typu kontejner. I když aplikace může mít více vláken, každá instance vloženého objektu bude přiřazena k jednomu "typu Apartment", který se spustí pouze v jednom vlákně. Jinými slovy, všechna volání do instance ovládacího prvku budou provedena ve stejném vlákně.

Různé instance stejného typu ovládacího prvku však mohou být přiřazeny k různým typům Apartment. Takže pokud více instancí ovládacího prvku sdílí jakákoli společná data (například statická nebo globální data), bude nutné přístup k těmto sdíleným datům chránit synchronizačním objektem, jako je například kritická část.

Úplné podrobnosti o modelu vláken Apartment naleznete v tématu [procesy a vlákna](/windows/win32/ProcThread/processes-and-threads) v *referenci programátora OLE*.

## <a name="why-support-apartment-model-threading"></a>Proč podpora vláken modelu apartment

Ovládací prvky, které podporují vlákna modelu apartment, lze použít ve vícevláknových aplikacích s více vlákny, které také podporují model Apartment. Pokud nepovolíte dělení na vlákna modelu apartment, omezíte potenciální sadu kontejnerů, ve kterých by byl ovládací prvek použit.

Povolení dělení modelu Apartment je snadné pro většinu ovládacích prvků, zejména v případě, že mají málo nebo žádná sdílená data.

## <a name="protecting-shared-data"></a>Ochrana sdílených dat

Pokud váš ovládací prvek používá sdílená data, například statickou členskou proměnnou, měl by být přístup k těmto datům chráněn s kritickou částí, aby se zabránilo více než jednomu vláknu v úpravě dat ve stejnou dobu. Chcete-li pro tento účel nastavit kritickou část, deklarujte statickou členskou proměnnou třídy `CCriticalSection` ve třídě ovládacího prvku. Používejte členské funkce `Unlock`atohoto objektu kritické sekce všude, kde váš kód přistupuje ke sdíleným datům. `Lock`

Vezměte v úvahu například třídu ovládacího prvku, která musí udržovat řetězec, který je sdílen všemi instancemi. Tento řetězec může být udržován ve statické členské proměnné a chráněný kritickým oddílem. Deklarace třídy ovládacího prvku by obsahovala následující:

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

Implementace třídy by zahrnovala definice těchto proměnných:

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

Přístup ke `_strShared` statickému členu lze následně ochránit pomocí kritické části:

```
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>Registrace ovládacího prvku pracujícího s modelem Apartment

Ovládací prvky, které podporují vlákno modelu apartment, by měly tuto schopnost označit v registru přidáním pojmenované hodnoty "ThreadingModel" s hodnotou "Apartment" v položce registru Class ID pod *ID* \\  **třídy. InprocServer32** klíč. Chcete-li způsobit, aby byl tento klíč automaticky zaregistrován pro váš ovládací prvek, předejte příznak *afxRegApartmentThreading* do `AfxOleRegisterControlClass`šestého parametru pro:

```
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)
{
    if (bRegister)
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(),
    m_clsid,
    m_lpszProgID,
    IDS_SAMPLE,
    IDB_SAMPLE,
    afxRegApartmentThreading,
    _dwSampleOleMisc,
    _tlid,
    _wVerMajor,
    _wVerMinor);

else
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}
```

Pokud váš projekt ovládacího prvku byl vygenerován pomocí ControlWizard C++ v jazyce Visual verze 4,1 nebo novější, tento příznak již bude ve vašem kódu přítomen. Pro registraci modelu vláken nejsou nutné žádné změny.

Pokud byl projekt vygenerován starší verzí ControlWizard, váš stávající kód bude mít logickou hodnotu jako šestý parametr. Pokud je stávající parametr TRUE, změňte ho na *afxRegInsertable | afxRegApartmentThreading*. Pokud je stávající parametr FALSE, změňte jej na *afxRegApartmentThreading*.

Pokud váš ovládací prvek nedodržuje pravidla pro podprocesy modelu apartment, nesmíte v tomto parametru předat *afxRegApartmentThreading* .

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
