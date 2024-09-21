## alfresco-content-services

### Case 1 : Default from https://github.com/Alfresco/acs-deployment/blob/master/docker-compose/community-docker-compose.yml

### Case 2 : Custome Nginx image, so we can remove dependencies on content-app which is not being used 
			`docker-compose up --build` (use this to re build the image after change in dockerFile)

### Issue-1:
1. 2024-09-19T21:51:41,215 [] ERROR [alfresco.web.site] [http-nio-8080-exec-2] jakarta.servlet.ServletException: Possible CSRF attack noted when asserting referer header 'http://localhost:8080/share/page'. Request: POST /share/page/dologin, FAILED TEST: Assert referer POST /share/page/dologin :: referer: 'http://localhost:8080/share/page' vs server & context: http://localhost/ (string) or  (regexp)
   - Fix: Add below under share, environment 
	` CSRF_FILTER_REFERER: "http://localhost(:[0-9]*)?/.*"    # Allow any port on localhost
          CSRF_FILTER_ORIGIN: "http://localhost:8080"             # Set origin for localhost`
     

