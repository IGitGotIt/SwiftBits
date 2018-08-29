# swiftBits
```Swift
//: Playground - noun: a place where people can play

import UIKit


enum Nucletoid: Character, Comparable {
    case A = "A", C = "C" , G = "G", T = "T"
    static func < (lhs:Nucletoid, rhs:Nucletoid) -> Bool {
        return lhs.rawValue < rhs.rawValue
    }
    static func > (lhs:Nucletoid, rhs:Nucletoid) -> Bool {
        return lhs.rawValue > rhs.rawValue
    }
    static func == (x:Nucletoid, y:Nucletoid) -> Bool {
        return x.rawValue == y.rawValue
    }
}

struct Codon : Comparable {
    private var a , b, c : Nucletoid;
    init(_ x: Nucletoid, _ y:Nucletoid , _ z: Nucletoid) {
        a = x; b = y; c = z ;
        }
    static func < (lhs: Codon, rhs: Codon) -> Bool {
        return (lhs.a,lhs.b,lhs.c) < (rhs.a, rhs.b, rhs.c)
    }
    static func > (lhs: Codon, rhs: Codon) -> Bool {
        return (lhs.a,lhs.b,lhs.c) > (rhs.a, rhs.b, rhs.c)
    }
    static func == (lhs: Codon, rhs: Codon) -> Bool {
        return (lhs.a,lhs.b,lhs.c) == (rhs.a, rhs.b, rhs.c)
    }
}

typealias Gene = [Codon]



var aaa: Codon = Codon(Nucletoid.A,Nucletoid.A,Nucletoid.A)
var ccc: Codon = Codon (Nucletoid.C,Nucletoid.C,Nucletoid.C)
var cct: Codon = Codon(Nucletoid.C,Nucletoid.C,Nucletoid.T)
var ctt: Codon = Codon(Nucletoid.C,Nucletoid.T,Nucletoid.T)

var aN = [ccc, cct, aaa]


func binaryContains<T: Comparable> (_ array: [T], item: T) -> Bool {
    var low = 0
    var high = array.count - 1
    while low <= high {
        let mid = (low + high)/2
        if array[mid] > item {
            high = mid - 1
        } else if array[mid] < item {
            low = mid + 1
        } else {
            return true
        }
    }
    return false
}

print("binary Contains = \(binaryContains(aN.sorted(by: <), item: cct))")
```
