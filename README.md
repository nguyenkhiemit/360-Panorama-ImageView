# 360-Panorama-ImageView

IOS: https://github.com/scihant/CTPanoramaView <br>
Android: https://github.com/gjiazhe/PanoramaImageView <br>

IOS: <br>
Download image from URL and display to ImageView and CTPanoramaView: <br>

    class ViewController: UIViewController {

        @IBOutlet weak var imageView: UIImageView!

        @IBOutlet weak var panoramaView: CTPanoramaView!

        override func viewDidLoad() {
            super.viewDidLoad()
            panoramaView.controlMethod = .touch
            let remoteImageURL = URL(string: "https://iphonephotographyschool.com/wp-content/uploads/iOS-6-Panorama1.jpg")!
             // Use Alamofire to download the image
             Alamofire.request(remoteImageURL).responseData { (response) in
                 if response.error == nil {
                     print(response.result)
                     // Show the downloaded image:
                     if let data = response.data {
                        self.imageView.image = UIImage(data: data)
                         self.panoramaView.image = UIImage(data: data)
                     }
                 }
             }
        }

        override var supportedInterfaceOrientations: UIInterfaceOrientationMask {
            return .all
        }
    }
