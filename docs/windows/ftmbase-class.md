---
title: Ftmbase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
dev_langs:
- C++
helpviewer_keywords:
- FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb3b9ecae955ac78c6139156c3379fcd97511671
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584370"
---
# <a name="ftmbase-class"></a>FtmBase – třída

Představuje objekt s volným zařazováním vláken.

## <a name="syntax"></a>Syntaxe

```cpp
class FtmBase : public Microsoft::WRL::Implements<
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
   Microsoft::WRL::CloakedIid<IMarshal> >;
```

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [runtimeclass – třída](runtimeclass-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[FtmBase::FtmBase – konstruktor](../windows/ftmbase-ftmbase-constructor.md)|Inicializuje novou instanci třídy **ftmbase –** třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[FtmBase::CreateGlobalInterfaceTable – metoda](../windows/ftmbase-createglobalinterfacetable-method.md)|Vytvoří globální tabulku rozhraní (GIT).|
|[FtmBase::DisconnectObject – metoda](../windows/ftmbase-disconnectobject-method.md)|Nuceně uvolní všechny externí připojení k objektu. Server objektu zavolá objektu implementace této metody před vypíná.|
|[FtmBase::GetMarshalSizeMax – metoda](../windows/ftmbase-getmarshalsizemax-method.md)|Získejte horní mez počtu bajtů potřebných k zařazování zadaný ukazatel rozhraní na zadaný objekt.|
|[FtmBase::GetUnmarshalClass – metoda](../windows/ftmbase-getunmarshalclass-method.md)|Získá identifikátor CLSID, který COM používá k nalezení knihovny DLL obsahující kód pro odpovídající server proxy. COM načte tuto knihovnu DLL vytvořit neinicializované instance serveru proxy.|
|[FtmBase::MarshalInterface – metoda](../windows/ftmbase-marshalinterface-method.md)|Zapíše do datového proudu data potřebná k inicializaci objektu proxy v nějaký proces klienta.|
|[FtmBase::ReleaseMarshalData – metoda](../windows/ftmbase-releasemarshaldata-method.md)|Zničí zařazené datový paket.|
|[FtmBase::UnmarshalInterface – metoda](../windows/ftmbase-unmarshalinterface-method.md)|Inicializuje nově vytvořeného serveru proxy a vrátí ukazatel rozhraní na tento server proxy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[FtmBase::marshaller_ – datový člen](../windows/ftmbase-marshaller-data-member.md)|Obsahuje odkaz na volné zařazování vláken.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FtmBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)