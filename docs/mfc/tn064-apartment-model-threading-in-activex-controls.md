---
title: 'TN064: Model apartment práce s vlákny v ovládacích prvcích ActiveX'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 0c6a42124b4b2b03ae7cd9277fa14d43eac7a2bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366059"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Model apartment práce s vlákny v ovládacích prvcích ActiveX

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato technická poznámka vysvětluje, jak povolit zřetězení apartment-model v ovládacím prvku ActiveX. Všimněte si, že apartment-model zřetězení je podporována pouze ve verzích Visual C++ 4.2 nebo novější.

## <a name="what-is-apartment-model-threading"></a>Co je apartment-model závitování

Model apartment je přístup k podpoře vložených objektů, jako jsou ovládací prvky ActiveX, v rámci aplikace kontejneru s více vlákny. Přestože aplikace může mít více vláken, každá instance vloženého objektu bude přiřazena k jednomu "apartment", který bude spuštěn pouze v jednom vlákně. Jinými slovy, všechna volání do instance ovládacího prvku dojde ve stejném vlákně.

Různé instance stejného typu ovládacího prvku však mohou být přiřazeny různým bytům. Pokud tedy více instancí ovládacího prvku sdílí všechna společná data (například statická nebo globální data), bude nutné přístup k těmto sdíleným datům chránit objekt synchronizace, například kritický oddíl.

Úplné podrobnosti o modelu apartment threading naleznete v [tématu Procesy a vlákna](/windows/win32/ProcThread/processes-and-threads) v *odkazu programátora OLE*.

## <a name="why-support-apartment-model-threading"></a>Proč podpora Apartment-Model závitování

Ovládací prvky, které podporují apartment-model podprocesu lze použít v aplikacích kontejneru s více vlákny, které také podporují model apartment. Pokud nepovolíte apartment-model zřetězení, omezíte potenciální sadu kontejnerů, ve kterých by mohl být použit ovládací prvek.

Povolení apartment-model zřetězení je snadné pro většinu ovládacích prvků, zejména v případě, že mají málo nebo žádná sdílená data.

## <a name="protecting-shared-data"></a>Ochrana sdílených dat

Pokud ovládací prvek používá sdílená data, jako je například statická členská proměnná, přístup k těmto datům by měl být chráněn kritickým oddílem, aby se zabránilo úpravám dat současně více než jedním vláknem. Chcete-li pro tento účel nastavit kritický oddíl, `CCriticalSection` deklarujte statickou členovou proměnnou třídy ve třídě ovládacího prvku. Použijte `Lock` a `Unlock` členské funkce tohoto objektu kritické části všude tam, kde váš kód přistupuje ke sdíleným datům.

Zvažte například třídu ovládacího prvku, která potřebuje udržovat řetězec, který je sdílen všemi instancemi. Tento řetězec lze udržovat ve statické členské proměnné a chráněny kritickým oddílem. Deklarace třídy ovládacího prvku by obsahovala následující:

```cpp
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

Implementace pro třídu by zahrnovala definice pro tyto proměnné:

```cpp
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

Přístup ke `_strShared` statickému členu pak může být chráněn kritickým oddílem:

```cpp
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>Registrace apartment-model-aware ovládacího prvku

Ovládací prvky, které podporují apartment-model podprocesu by měl y oznamovat tuto schopnost v registru přidáním pojmenované hodnoty "ThreadingModel" s hodnotou "Apartment" v jejich vstupu do registru ID třídy pod *třídou id*\\**InprocServer32** klíč. Chcete-li způsobit, že tento klíč bude automaticky zaregistrován pro váš ovládací `AfxOleRegisterControlClass`prvek, předejte příznak *afxRegApartmentThreading* v šestém parametru :

```cpp
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

Pokud váš řídicí projekt byl generován ControlWizard v jazyce Visual C++ verze 4.1 nebo novější, tento příznak již bude k dispozici ve vašem kódu. Žádné změny jsou nutné k registraci modelu podprocesu.

Pokud byl projekt vygenerován starší verzí Průvodce ovládáním, bude mít existující kód jako šestý parametr logickou hodnotu. Pokud je existující parametr TRUE, změňte jej na *afxRegInsertable | afxRegApartmentThreading*. Pokud je existující parametr FALSE, změňte jej na *afxRegApartmentThreading*.

Pokud váš ovládací prvek nedodržuje pravidla pro apartment-model zřetězení, nesmíte předat *afxRegApartmentThreading* v tomto parametru.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
