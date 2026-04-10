# GitHub Finder
 
> Search any GitHub profile and instantly explore their top repositories — built with React, TypeScript, and the GitHub public API.
 
[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev/)
[![GitHub API](https://img.shields.io/badge/GitHub_API-Public-181717?style=for-the-badge&logo=github&logoColor=white)](https://docs.github.com/en/rest)


![Project Demo](https://github.com/Luan-Neumann-Dev/GitHubFinder/assets/155394874/56d48d3d-287d-4001-85b5-1c271b406c74)
![Project Demo](https://github.com/Luan-Neumann-Dev/GitHubFinder/assets/155394874/5f05f6c3-64d1-4605-98c2-dbd5def5e329)
![Project Demo](https://github.com/Luan-Neumann-Dev/GitHubFinder/assets/155394874/e73e1789-e3c6-404f-8f53-3fed474bd7bf)

**[🚀 View Live Demo](https://github-finder-lemon-eight.vercel.app/)**

## 🎯 About
 
GitHub Finder is a React SPA that lets you search any GitHub user by username and instantly view their public profile data — avatar, location, follower count and following count. From the profile view, you can navigate to that user's top 5 most-starred repositories, all fetched in real time from the GitHub public API.
 
The project was built to practice integrating a real-world REST API with React, while applying TypeScript for type safety across components and data flows.
 
## ✨ Key Features
 
- 🔎 **User Search** - Search any GitHub username and retrieve live profile data from the GitHub API
- 👤 **Profile Overview** - Displays avatar, username, location, followers, and following count
- ⭐ **Top Repositories** - Lists the 5 most-starred public repositories of the searched user
- ⚡ **Loading States** - Loader component displayed during API requests for smooth UX
- 🚫 **Error Handling** - User-friendly error screen when a profile is not found (404)
- 🧭 **Client-side Routing** - Seamless navigation between search and repository pages via React Router
 
## 🛠️ Tech Stack

**Frontend:**
- React 18 — Component architecture and state management with hooks
- TypeScript — Static typing for props, API responses, and component interfaces
- React Router DOM v6 — Client-side routing between the home and repos pages
- React Icons — Icon library for UI elements (search icon, location pin)
- CSS Modules — Scoped, component-level styling
 
**Build Tool:**
- Vite — Fast dev server and optimized production bundler
 
**External API:**
- GitHub REST API (public) — User profiles and repository data
 
## 🚀 Quick Start
```bash
# Clone the repository
git clone https://github.com/Luan-Neumann-Dev/GitHubFinder.git
 
# Navigate to project
cd GitHubFinder
 
# Install dependencies
npm install
 
# Start the dev server
npm run dev
```

Then open [http://localhost:5173](http://localhost:5173) in your browser.
 
Or visit the **[live demo →](https://github-finder-lemon-eight.vercel.app/)**
 
## 📁 Project Structure

```
GitHubFinder/
├── src/
│   ├── components/         # Reusable UI components
│   │   ├── Search.tsx      # Search input + trigger
│   │   ├── User.tsx        # Profile card display
│   │   ├── Repo.tsx        # Repository card
│   │   ├── Loader.tsx      # Loading spinner
│   │   ├── BackBtn.tsx     # Back navigation button
│   │   └── Error.tsx       # Error feedback component
│   ├── routes/             # Page-level components
│   │   ├── Home.tsx        # Search page + API call logic
│   │   └── Repos.tsx       # Top repositories page
│   ├── types/              # TypeScript interfaces
│   │   ├── user.ts         # UserProps type
│   │   └── repo.ts         # RepoProps type
│   ├── App.tsx             # Root component with router outlet
│   └── main.tsx            # Entry point
├── index.html
├── vite.config.ts
└── tsconfig.json
```

## 💡 Technical Highlights
 
### GitHub API Integration with TypeScript
API responses are consumed via native `fetch` and typed with custom interfaces, making data handling predictable across all components.
 
```typescript
// src/types/user.ts
export type UserProps = {
  avatar_url: string;
  login: string;
  location: string;
  followers: number;
  following: number;
};
```

### Sorting Repos by Stars on the Client
Instead of relying on API query params, repos are sorted client-side and sliced to the top 5 — keeping the implementation simple and avoiding additional API calls.
 
```typescript
let orderedRepos = data.sort((a: RepoProps, b: RepoProps) =>
  b.stargazers_count - a.stargazers_count
);
orderedRepos = orderedRepos.slice(0, 5);
```
## 📚 What I Learned
 
**Technical Skills:**
- Consuming a real REST API with `fetch` and handling different response statuses (200, 404)
- Applying TypeScript interfaces to type API responses and component props end-to-end
- Setting up client-side routing with React Router v6 (`<Outlet>`, `useParams`)
- Using CSS Modules to keep styles scoped and avoid naming conflicts
 
**Best Practices:**
- Managing UI states (loading, error, data) explicitly with separate `useState` flags
- Separating data-fetching logic (routes) from presentational components
- Typing props strictly to catch integration errors at compile time
 
## 🗺️ Roadmap
 
- [ ] Add pagination for repositories instead of limiting to top 5
- [ ] Display repository details: language, last updated, description
- [ ] Support keyboard navigation (already handles Enter key in search)
- [ ] Add dark/light theme toggle
- [ ] Cache recent searches to reduce repeated API calls
 
## 📝 Notes
 
- No authentication is used — the app relies on the GitHub public API (rate-limited to 60 req/hour per IP)
- Not affiliated with GitHub, Inc.
 
## 📄 License
 
MIT License - see [LICENSE](LICENSE) for details.
 
## 👤 Author
 
**Luan Neumann**
 
- LinkedIn: [luan-neumann-dev](https://www.linkedin.com/in/luan-neumann-dev/)
- GitHub: [@Luan-Neumann-Dev](https://github.com/Luan-Neumann-Dev)
 
---
 
⭐ Found this helpful? Give it a star!
