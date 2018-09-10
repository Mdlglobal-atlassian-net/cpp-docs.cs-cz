---
title: Integrace modulu CLR (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95dd817e7081eea6371e9dab9d95aec06d22971c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110763"
---
# <a name="clr-integration-ccx"></a>Integrace modulu CLR (C + +/ CX)

Některé typy Windows Runtime přijímat zvláštní zpracování v jazyce C + +/ CX a jazyky, které jsou založené na common language runtime (CLR). Tento článek popisuje, jak několika typy v jednom jazyce mapují na jiný jazyk. Například modul CLR mapuje Windows.Foundation.IVector rozhraní System.Collections.IList, Windows.Foundation.IMap rozhraní System.Collections.IDictionary a tak dále. Obdobně C + +/ CX speciálně mapuje typy, jako jsou Platform::Delegate – a Platform::String.

## <a name="mapping-the-windows-runtime-to-ccx"></a>Mapování modulu Windows Runtime pro C + +/ CX

Když C + +/ CX přečte soubor metadat (.winmd) pro Windows, kompilátor automaticky mapují běžné obory názvů Windows Runtime a typy pro C + +/ CX obory názvů a typů. Například číselný typ Windows Runtime `UInt32` automaticky se namapuje na `default::uint32`.

C + +/ CX mapuje několik dalších typů modulu Windows Runtime na **platformy** oboru názvů. Například **Windows::Foundation –** popisovače HSTRING, který reprezentuje textový řetězec Unicode jen pro čtení, je namapována na C + +/ CX `Platform::String` třídy. Při operaci Windows Runtime vrátí chybu HRESULT, je namapována na C + +/ CX `Platform::Exception`.

C + +/ CX také mapuje určité typy v oborech názvů Windows Runtime k vylepšení typu funkce. Pro tyto typy, C + +/ CX poskytuje pomocné rutiny konstruktorů a metod, které jsou specifické pro C++ a nejsou k dispozici v souboru .winmd standardní tohoto typu.

Následující seznamy shrnují struktuře hodnot, které podporují nové konstruktory a metody helper. Pokud jste dřív napsali kód, který používá struktury inicializační seznamy, změňte ji na použití nově přidané konstruktory.

**Windows::Foundation –**

- Bod

- Rect

- Velikost

**Windows::UI**

- Barva

**Windows::UI::XAML**

- CornerRadius

- Doba trvání

- GridLength

- Tloušťka

**Windows::UI::Xaml::Interop**

- TypeName

**Windows::UI::Xaml::Media**

- matice

**Windows::UI::XAML::Media::Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>Mapování modulu CLR pro C + +/ CX

Při čtení souboru .winmd kompilátory jazyka Visual C++ nebo C# mapují automaticky určitých typů v souboru metadat pro příslušné C + +/ CX nebo CLR typy. Například v prostředí CLR IVector\<T > rozhraní je namapována na IList\<T >. Ale v jazyce C + +/ CX, IVector\<T > rozhraní není namapována na jiného typu.

IReference\<T > v modulu Windows Runtime mapuje na Nullable\<T > v rozhraní .NET.

## <a name="see-also"></a>Viz také

[Spolupráce s jinými jazyky](../cppcx/interoperating-with-other-languages-c-cx.md)