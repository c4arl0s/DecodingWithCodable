# DecodingWithCodable
DecodingWithCodable

``` swift
import Foundation

struct Note: Codable {
    let title: String
    let text: String
    let timestamp: Date
}
```
``` swift
import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        let newNote = Note(title: "new note", text: "this is a new note", timestamp: Date())
        // first encoding
        let propertyListEncoder = PropertyListEncoder()
        if let encodedNote = try? propertyListEncoder.encode(newNote) {
            print(encodedNote)
            print("it prints the number of bytes stored in the Data Object")
            // then decoding what encoded before
            let propertyListDecoder = PropertyListDecoder()
            if let decodedNote = try? propertyListDecoder.decode(Note.self, from: encodedNote) {
                print(decodedNote)
                print("as you can see decodedNote is the structure note")
            }
        }
    }
}
```


