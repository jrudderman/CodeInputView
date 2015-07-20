# CodeInputView

4-Digit Code Input Text Field

![Screenshots][1]

## Instructions

1. Follow these [instructions on how to add a Git repository to your Xcode project][2].

2. Usage

        import UIKit

        class EnterCodeViewController: UIViewController, CodeInputViewDelegate, UIAlertViewDelegate {
            // MARK: - UIViewController

            override func viewDidLoad() {
                super.viewDidLoad()

                let codeInputView = CodeInputView(frame: CGRect(x: (view.frame.width-215)/2, y: 242, width: 215, height: 60))
                codeInputView.delegate = self
                codeInputView.tag = 17
                view.addSubview(codeInputView)

                codeInputView.becomeFirstResponder()
            }

            // MARK: - CodeInputViewDelegate

            func codeInputView(codeInputView: CodeInputView, didFinishWithCode code: String) {
                let title = code == "1234" ? "Correct!" : "Wrong!"
                let alertView = UIAlertView(title: title, message: nil, delegate: self, cancelButtonTitle: "OK")
                alertView.show()
            }

            // MARK: - UIAlertViewDelegate

            func alertView(alertView: UIAlertView, clickedButtonAtIndex buttonIndex: Int) {
                (view.viewWithTag(17) as! CodeInputView).clear()
            }
        }

Released under the [Unlicense][3].


[1]: Screenshots.gif
[2]: https://github.com/acani/Libraries
[3]: http://unlicense.org
