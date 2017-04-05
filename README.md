# CollectionView-UIButton-UISegmentedControl-Listen-to-click
Swift 3, CollectionView


    override func collectionView(_ collectionView: UICollectionView, viewForSupplementaryElementOfKind kind: String, at indexPath: IndexPath) -> UICollectionReusableView {
        let header = collectionView.dequeueReusableSupplementaryView(ofKind: kind, withReuseIdentifier: headerId, for: indexPath) as! AppDetailHeader
        header.app = app

        header.segmentedControl.addTarget(self, action: #selector(segmentedControlAction(sender:)), for: UIControlEvents.valueChanged)
        
        return header
    }
    
    func segmentedControlAction(sender: UISegmentedControl) {
        
        switch sender.selectedSegmentIndex {
        case 0:
            segmentControl = 0
            collectionView?.reloadData()
        case 1:
            segmentControl = 1
            collectionView?.reloadData()
        case 2:
            segmentControl = 2
            collectionView?.reloadData()
        default:
            break
        }
    }


    let segmentedControl: UISegmentedControl = {
        let sc = UISegmentedControl(items: ["Details","Review","Related"])
        sc.tintColor = UIColor.darkGray
        sc.selectedSegmentIndex = 0
        return sc
    }()
    
        let myButton: UIButton = {
        let button = UIButton(type: .system)
        button.setTitle("Ok", for: UIControlState())
        button.layer.borderColor = UIColor(red: 0, green: 129/255, blue: 250/255, alpha: 1).cgColor
        button.layer.borderWidth = 1
        button.layer.cornerRadius = 5
        button.titleLabel?.font = UIFont.boldSystemFont(ofSize: 14)
        return button
    }()
    
    override func setupViews(){
        super.setupViews()

        addSubview(myButton)
        addSubview(segmentedControl)
        
        addConstraintsWithFormat("H:|-40-[v0]-40-|", views: segmentedControl)
        addConstraintsWithFormat("V:[v0(34)]-8-|", views: segmentedControl)
        
        addConstraintsWithFormat("H:[v0(60)]-14-|", views: myButton)
        addConstraintsWithFormat("V:[v0(32)]-56-|", views: myButton)
    }
    
    
