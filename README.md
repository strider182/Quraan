# Reading Coordination Project

A real-time web application for coordinating reading assignments among multiple participants using Firebase Firestore.

## Features

- **Real-time collaboration**: Multiple users can claim reading portions simultaneously
- **Conflict prevention**: Automatic detection when someone else claims a portion you're selecting
- **Progress tracking**: Visual progress bar and completion timeline
- **Offline fallback**: Works offline using localStorage as backup
- **Mobile responsive**: Works on desktop and mobile devices

## Demo

![Reading Coordination Interface](https://via.placeholder.com/800x400/4bbf73/ffffff?text=Reading+Coordination+Project)

## Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/reading-coordination.git
   cd reading-coordination
   ```

2. **Set up Firebase** (see [Firebase Setup Guide](firebase-setup.md))
   - Create a Firebase project
   - Enable Firestore database
   - Get your Firebase config
   - Update `coordination.html` with your config

3. **Open the app**
   - Simply open `coordination.html` in your web browser
   - No build process or server required!

## How It Works

1. **Claim portions**: Enter your name, select a completion date, choose reading portions, and claim them
2. **Real-time updates**: See other participants' claims instantly
3. **Track progress**: Mark portions as complete and view overall progress
4. **Coordinate deadlines**: See completion timeline and estimated project finish date

## Project Structure

```
reading-coordination/
├── coordination.html      # Main application file
├── firebase-setup.md     # Firebase configuration guide
├── README.md            # This file
└── .gitignore          # Git ignore file
```

## Firebase Configuration

The app uses Firebase Firestore for real-time data synchronization. See [firebase-setup.md](firebase-setup.md) for detailed setup instructions.

## Data Structure

- **Collection**: `projects`
- **Document**: `reading-coordination`
- **Fields**:
  - `portions`: Array of 30 reading portions
  - `readers`: Object mapping reader names to assignments
  - `lastUpdated`: Timestamp for conflict detection

## Browser Support

- Chrome (recommended)
- Firefox
- Safari
- Edge

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

MIT License - feel free to use this project for your reading groups!

## Support

If you encounter issues:
1. Check the browser console for errors
2. Verify your Firebase configuration
3. Ensure Firestore is in test mode for development
4. Open an issue on GitHub

---

**Made for reading groups who want to coordinate their progress in real-time!**