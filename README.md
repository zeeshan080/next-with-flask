1. Create Nextjs 13 project

npx create-next-app@latest

2. check python installation and create virtual envoirnment and activate it

python --version
python -m venv venv (any name you want)

3. check pip version and packages and install flask

pip --version
pip list
pip install flask

4. create api directory in root folder and index.py

(in root of your folder)

	-src
	-api
	  -index.py

5. install concurrently

npm install concurrently

6. add scripts update in package.json

"flask-dev": "python -m flask --app api/index run -p 8000 --reload",
"next-dev": "next dev",
"dev": "concurrently \"npm run next-dev\" \"npm run flask-dev\"",

7. proxy request at localhost:3000 to 127.0.0.1:8080

/** @type {import('next').NextConfig} */
const nextConfig = {
    rewrites: async () => {
        return [
        {
            source: '/api/:path*',
            destination:
            process.env.NODE_ENV === 'development'
                ? 'http://127.0.0.1:8000/api/:path*'
                : '/api/',
        },
        ]
  },
}

module.exports = nextConfig

8. run project and verify that flask api is working

9. create routes for CRUD in api

10. add zustand and create store folder

11. create frontend for the todo with shadcnui

npx shadcn-ui@latest init

12. link state update from frontend to api using zustand
